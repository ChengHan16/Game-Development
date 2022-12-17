### note
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class PlayerHealthBar : MonoBehaviour
{
    public Text healthText;
    public static int HealthCurrent;
    public static int HealthMax;

    private Image healthBar;

    void Start()
    {
        healthBar = GetComponent<Image>();

        //HealthCurrent = HealthMax;
    }

    void Update()
    {
        healthBar.fillAmount = (float)HealthCurrent / (float)HealthMax;
        healthText.text = HealthCurrent.ToString() + "/" + HealthMax.ToString();
    }
}
```
### 2022-12-18 EnemyBoss (Script-Back-Up) [04:33 a.m]
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EnemyBoss : MonoBehaviour
{
    bool isAlive, isIdle, jumpAttact, isJumpUp, slideAttact, isHurt, canBeHurt;
    public int life;
    public float attactDistance, jumpHeight, jumpUpSpeed, jumpDownSpeed, slideSpeed,fallDownSpeed;

    [Header("CanBeHurt")]
    public float CanBeHurtTime;

    GameObject player;
    Animator myAnim;
    BoxCollider2D myCollider;
    SpriteRenderer mySr;

    Vector3 slideTargetPosition;

    private void Awake()
    {
        isAlive = true;
        isIdle = true;
        isHurt = false;
        jumpAttact = false;
        isJumpUp = true;
        slideAttact = false;
        canBeHurt = true;

        player = GameObject.Find("Player");
        myAnim = GetComponent<Animator>();
        myCollider = GetComponent<BoxCollider2D>();
        mySr = GetComponent<SpriteRenderer>();
    }

    private void Start()
    {
        BossLife.HealthCurrent = life;
        BossLife.HealthMax = life;
    }

    void Update()
    {
        if (isAlive)
        {
            if (isIdle)
            {
                LookAtPlayer();

                if (Vector3.Distance(player.transform.position, transform.position) <= attactDistance)
                {
                    isIdle = false;
                    StartCoroutine("IdleToSlideAttact");
                }
                else
                {
                    isIdle = false;
                    StartCoroutine("IdleToJumpAttact");
                }
            }
            else if (jumpAttact)
            {
                LookAtPlayer();

                if (isJumpUp)
                {
                    Vector3 myTarget = new Vector3(player.transform.position.x, jumpHeight, transform.position.z);
                    transform.position = Vector3.MoveTowards(transform.position, myTarget, jumpUpSpeed * Time.deltaTime);

                    myAnim.SetBool("JumpUp", true);
                }
                else
                {
                    myAnim.SetBool("JumpUp", false);
                    myAnim.SetBool("JumpDown", true);

                    Vector3 myTarget = new Vector3(transform.position.x, -14.55f, transform.position.z);
                    transform.position = Vector3.MoveTowards(transform.position, myTarget, jumpDownSpeed * Time.deltaTime);
                }

                if (transform.position.y == jumpHeight)
                {
                    isJumpUp = false;
                }
                else if (transform.position.y == -14.55f)
                {
                    jumpAttact = false;
                    StartCoroutine("JumpDownToIdle");
                }
            }
            else if (slideAttact)
            {
                myAnim.SetBool("Slide", true);
                transform.position = Vector3.MoveTowards(transform.position, slideTargetPosition, slideSpeed * Time.deltaTime);

                if (transform.position == slideTargetPosition)
                {
                    myCollider.offset = new Vector2(-0.008521557f, 0.009188652f);
                    myCollider.size = new Vector2(0.8707628f, 2.879219f);
                    myAnim.SetBool("Slide", false);
                    slideAttact = false;
                    isIdle = true;
                }
            }
            else if (isHurt)
            {
                Vector3 myTagetPosition = new Vector3(transform.position.x, -14.55f, transform.position.z);
                transform.position = Vector3.MoveTowards(transform.position, myTagetPosition, fallDownSpeed * Time.deltaTime);
            }
        }
        else
        {
            Vector3 myTagetPosition = new Vector3(transform.position.x, -14.55f, transform.position.z);
            transform.position = Vector3.MoveTowards(transform.position, myTagetPosition, fallDownSpeed * Time.deltaTime);
        }
    }

    void LookAtPlayer()
    {
        if (player.transform.position.x > transform.position.x)
        {
            transform.localScale = new Vector3(1.0f, 1.0f, 1.0f);
        }
        else
        {
            transform.localScale = new Vector3(-1.0f, 1.0f, 1.0f);
        }
    }

    IEnumerator JumpDownToIdle()
    {
        yield return new WaitForSeconds(0.2f);
        isIdle = true;
        isJumpUp = true;
        myAnim.SetBool("JumpUp", false);
        myAnim.SetBool("JumpDown", false);
    }

    IEnumerator IdleToJumpAttact()
    {
        yield return new WaitForSeconds(0.5f);
        jumpAttact = true;
    }

    IEnumerator IdleToSlideAttact()
    {
        yield return new WaitForSeconds(1.5f);
        myCollider.offset = new Vector2(-0.008521557f, -0.8256693f);
        myCollider.size = new Vector2(0.8707628f, 1.209503f);
        slideTargetPosition = new Vector3(player.transform.position.x + 0.5f, transform.position.y, transform.position.z);
        LookAtPlayer();
        slideAttact = true;
    }

    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.tag == "PlayerAttact")
        {
            if (canBeHurt)
            {
                life--;
                BossLife.HealthCurrent = life;
                isHurtClass();
                if (life >= 1)
                {

                    isIdle = false;
                    jumpAttact = false;
                    slideAttact = false;
                    isHurt = true;

                    StopCoroutine("JumpDownToIdle");
                    StopCoroutine("IdleToJumpAttact");
                    StopCoroutine("IdleToSlideAttact");
                    myAnim.SetBool("Hurt", true);
                    Invoke("SetAnimHurtToFalse", 1.0f);
                    Invoke("CanBeHurt", CanBeHurtTime);
                }
                else
                {
                    isAlive = false;
                    myCollider.enabled = false;
                    StopAllCoroutines();
                    myAnim.SetBool("Die", true);

                    Time.timeScale = 0.2f;
                    Time.fixedDeltaTime = 0.002F * Time.timeScale;
                    StartCoroutine("AfterDie");
                }
                canBeHurt = false;
            }
        }

        if (collision.tag == "PlayerAttactForm3")
        {
            if (canBeHurt)
            {
                life-=50;
                BossLife.HealthCurrent = life;
                if (life >= 1)
                {

                    isIdle = false;
                    jumpAttact = false;
                    slideAttact = false;
                    isHurt = true;

                    StopCoroutine("JumpDownToIdle");
                    StopCoroutine("IdleToJumpAttact");
                    StopCoroutine("IdleToSlideAttact");
                    myAnim.SetBool("Hurt", true);
                    Invoke("SetAnimHurtToFalse", 1.0f);
                    Invoke("CanBeHurt", CanBeHurtTime);
                }
                else
                {
                    isAlive = false;
                    myCollider.enabled = false;
                    StopAllCoroutines();
                    myAnim.SetBool("Die", true);

                    Time.timeScale = 0.2f;
                    Time.fixedDeltaTime = 0.002F * Time.timeScale;
                    StartCoroutine("AfterDie");
                }
                canBeHurt = false;
            }
        }
    }

    void SetAnimHurtToFalse()
    {
        myAnim.SetBool("Hurt", false);
        myAnim.SetBool("JumpUp", false);
        myAnim.SetBool("JumpDown", false);
        myAnim.SetBool("Slide", false);

        mySr.material.color = new Color(1.0f, 1.0f, 1.0f, 0.5f);
        isHurt = false;
        isIdle = true;
    }

    void CanBeHurt()
    {
        canBeHurt = true;
        mySr.material.color = new Color(1.0f, 1.0f, 1.0f, 1.0f);
    }

    IEnumerator AfterDie()
    {
        yield return new WaitForSecondsRealtime(3.0f);
        FadeInOut.instance.SceneFadeInOut("MainMenu");
    }
}
```


### Report
------------------------------------------------------------------
### Title
1.
> Unity 2D Platform Action-adventure game [Prologue] <br>
>> Unity 2D 平台動作冒險遊戲 [序章] <br>
2.
> Unity 2D Flat Action-adventure game [Prologue] <br>
>> Unity 2D 平面動作冒險遊戲 [序章] <br>
3.
> Unity 2D Plane Action-adventure game [Prologue] <br>
>> Unity 2D 平面動作冒險遊戲 [序章] <br>
------------------------------------------------------------------
Title 參考資料： <br>
[平台遊戲/Platform game](https://zh.wikipedia.org/wiki/%E5%B9%B3%E5%8F%B0%E6%B8%B8%E6%88%8F) <br>
[橫向捲軸遊戲/Side-scrolling video game](https://zh.wikipedia.org/wiki/%E6%A9%AB%E5%90%91%E6%8D%B2%E8%BB%B8%E9%81%8A%E6%88%B2)


### PlayerPrefs
PlayerPrefs 參考資料：
[Unity 中保存遊戲數據的不同方法/Breaking Down the Different Ways to Save Game Data in Unity](https://www.gamedesigning.org/learn/unity-save-game/#Fundamental-Unity-Save-Game-Concepts)

### 遊戲硬體參考
[ICEY](https://store.steampowered.com/app/553640/ICEY/)
------------------
### [Smooth Slider Bar In Unity (JUST ONE LINE OF CODE) - Mathf.SmoothDamp()](https://www.youtube.com/watch?v=VZ1EAHLd24M)
### [Character Selection (And changing scene) - Unity 3D[Tutorial][C#]](https://www.youtube.com/watch?v=IFTjcPvCZaM&list=PLD078QdocaDaGgg2hKEtNZXtZhQMxUAFs&index=2&t=8s)
### [Unity Character/Skin Selection Menu - Easy Unity Tutorial](https://www.youtube.com/watch?v=2PKBChN10us&list=PLD078QdocaDaGgg2hKEtNZXtZhQMxUAFs&index=2)
### [FIRST PERSON MOVEMENT in Unity - FPS Controller](https://www.youtube.com/watch?v=_QajrabyTJc)
