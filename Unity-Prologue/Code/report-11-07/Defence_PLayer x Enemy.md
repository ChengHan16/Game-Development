### PlayerDefenceCollider
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Events;

public class PlayerDefenseCollider : MonoBehaviour
{
    Player playerScript;

    private void Awake()
    {
        playerScript = GetComponentInParent<Player>();
    }

    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.tag == "EnemyAttact")
        {
            Debug.Log(" ----- EnemyAttact -----");
            playerScript.isAterDefenes = true;
            Invoke("IsAfterDefenes",0.5f);
        }
    }

    void IsAfterDefenes()
    {
        Debug.Log(" ----- IsAfterDefenes -----");
        playerScript.isAterDefenes = false;
    }
}
```
### EnemyForm1
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EnemyTEST : MonoBehaviour
{
    public Vector3 targetPosition;
    public float mySpeed;
    public GameObject attactCollider, myGroundCollider;
    public int enemyLife;

    public Animator myAnim;
    public Vector3 originPosition, trunPoint;

    [HideInInspector]
    public bool IsFirstTimeIdle, IsAfterBattleCheck, IsAlive;

    protected GameObject myPlayer;
    BoxCollider2D myCollider;
    SpriteRenderer mySr;
    public Rigidbody2D myRigi;
    AttactCollider EnemyBDScript;
    EnemyLife myHealthScript;
    AudioSource myAudioSource;

    protected virtual void Awake()
    {
        EnemyBDScript = GetComponentInParent<AttactCollider>();
        myHealthScript = GetComponentInParent<EnemyLife>();

        myAnim = GetComponent<Animator>();
        myCollider = GetComponent<BoxCollider2D>();
        mySr = GetComponent<SpriteRenderer>();
        myRigi = GetComponent<Rigidbody2D>();
        myAudioSource = GetComponent<AudioSource>();
        myPlayer = GameObject.Find("Player");
        originPosition = new Vector3(transform.position.x, transform.position.y, transform.position.z);

        IsFirstTimeIdle = true;
        IsAfterBattleCheck = false;
        IsAlive = true;
    }

    void Start()
    {
        EnemyLife.HealthCurrent = enemyLife;
        EnemyLife.HealthMax = enemyLife;
    }

    void Update()
    {
        MoveAndAttact();
    }

    protected virtual void MoveAndAttact()
    {
        if (IsAlive)
        {
            if (Vector3.Distance(myPlayer.transform.position, transform.position) < 2.0f)
            {
                if (myPlayer.transform.position.x <= transform.position.x)
                {
                    transform.localScale = new Vector3(-1.0f, 1.0f, 1.0f);
                }
                else
                {
                    transform.localScale = new Vector3(1.0f, 1.0f, 1.0f);
                }

                if (myAnim.GetCurrentAnimatorStateInfo(0).IsName("Attact") || myAnim.GetCurrentAnimatorStateInfo(0).IsName("AttactWait"))
                {
                    return;
                }
                myAnim.SetTrigger("Attact");
                StartCoroutine("ResetAttactTrigger");
                IsAfterBattleCheck = true;
                return;
            }
            else
            {
                if (IsAfterBattleCheck)
                {
                    if (trunPoint == targetPosition)
                    {
                        StartCoroutine(AfterAttactstoptime(true));
                    }
                    else if (trunPoint == originPosition)
                    {
                        StartCoroutine(AfterAttactstoptime(false));
                    }
                    IsAfterBattleCheck = false;
                }
            }

            if (transform.position.x == targetPosition.x)
            {
                myAnim.SetTrigger("Idle");
                trunPoint = originPosition;
                StartCoroutine(TurnRight(true));
                IsFirstTimeIdle = false;
            }
            else if (transform.position.x == originPosition.x)
            {
                if (!IsFirstTimeIdle)
                {
                    myAnim.SetTrigger("Idle");
                }
                trunPoint = targetPosition;
                StartCoroutine(TurnRight(false));
            }

            if (myAnim.GetCurrentAnimatorStateInfo(0).IsName("Walk"))
            {
                transform.position = Vector3.MoveTowards(transform.position, trunPoint, mySpeed * Time.deltaTime);
            }
        }
    }

    public IEnumerator TurnRight(bool turnRight)
    {
        if (turnRight)
        {
            yield return new WaitForSeconds(2.0f);
            transform.localScale = new Vector3(1.0f, 1.0f, 1.0f);
        }
        else if (!turnRight)
        {
            yield return new WaitForSeconds(2.0f);
            transform.localScale = new Vector3(-1.0f, 1.0f, 1.0f);
        }
    }

    protected IEnumerator AfterAttactstoptime(bool seetop)
    {
        if (seetop)
        {
            yield return new WaitForSeconds(2.0f);
            transform.localScale = new Vector3(-1.0f, 1.0f, 1.0f);
        }
        else if (!seetop)
        {
            yield return new WaitForSeconds(2.0f);
            transform.localScale = new Vector3(1.0f, 1.0f, 1.0f);
        }
    }

    IEnumerator ResetAttactTrigger()
    {
        yield return new WaitForSeconds(0.5f);
        myAnim.ResetTrigger("Attact");
    }

    public void SetAttactColliderOn()
    {
        attactCollider.SetActive(true);
    }
    public void SetAttactColliderPositionChang()
    {
        attactCollider.gameObject.GetComponent<BoxCollider2D>().offset = new Vector2(1.5f, 0);
    }

    public void SetAttactColliderOff()
    {
        attactCollider.SetActive(false);
        attactCollider.gameObject.GetComponent<BoxCollider2D>().offset = new Vector2(0.8f, 0);
    }

    protected virtual void OnTriggerEnter2D(Collider2D collision)
    {
        enemyLife--;
        EnemyLife.HealthCurrent = enemyLife;
        if (collision.tag == "PlayerAttact")
        {
            myAudioSource.PlayOneShot(myAudioSource.clip);
            if (enemyLife >= 1)
            {
                myAnim.SetTrigger("Hurt");
            }
            else if (enemyLife < 1)
            {
                IsAlive = false;
                myCollider.enabled = false;
                //myGroundCollider.SetActive(false);
                myAnim.SetTrigger("Die");
                StartCoroutine("AfterDie");
            }
        }
    }
    IEnumerator AfterDie()
    {
        yield return new WaitForSeconds(0.5f);
        mySr.material.color = new Color(mySr.color.r, mySr.color.g, mySr.color.b, 0.5f);
        //Animation 中有變更 α 值就得使用 mySr.Material.color API，若無 mySr.color 即可。
        //mySr.color = new Color(1.0f, 1.0f, 1.0f, 0.5f);

        yield return new WaitForSeconds(0.5f);
        mySr.material.color = new Color(mySr.color.r, mySr.color.g, mySr.color.b, 0.2f);

        yield return new WaitForSeconds(0.5f);
        Destroy(this.gameObject);
    }
}
```
### EnemyBreakDefenes
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Events;

public class EnemyBreakDefenes : MonoBehaviour
{
    public string newTag, trunTag;
    //public Text TagText;

    EnemyForm1 Enemyform1Script;

    private void Start()
    {
        gameObject.tag = "EnemyAttact";
    }

    private void Awake()
    {
        Enemyform1Script = GetComponentInParent<EnemyForm1>();

        gameObject.GetComponent<BoxCollider2D>().offset = new Vector2(0.8f, 0);
    }

    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.tag == "Playerdefenes")
        {
            if (collision.gameObject.tag == "Playerdefenes")
            {
                //Debug.Log("------- OnCollisionEnter2D -------");
                if (Enemyform1Script.transform.localScale.x == 1.0f)
                {
                    Enemyform1Script.myRigi.velocity = new Vector2(-5.0f, 5.0f);
                }
                else if (Enemyform1Script.transform.localScale.x == -1.0f)
                {
                    Enemyform1Script.myRigi.velocity = new Vector2(5.0f, 5.0f);
                }

                if (transform.position.x == Enemyform1Script.targetPosition.x)
                {
                    StartCoroutine(TurnRight(true));
                }
                else if (transform.position.x == Enemyform1Script.originPosition.x)
                {
                    StartCoroutine(TurnRight(false));
                }

                gameObject.tag = newTag;
                //TagText.text = newTag;
                Invoke("turnTag",0.5f);
                Enemyform1Script.myAnim.SetBool("Attact",false);
                Enemyform1Script.myAnim.ResetTrigger("Attact");
            }
            Enemyform1Script.myAnim.SetTrigger("Breakdefenes");
            AttactDefenes();
            Invoke("TimeRun",0.5f);
        }
    }

    void AttactDefenes()
    {
        Time.timeScale = 0.5f;
        Time.fixedDeltaTime = 0.002F * Time.timeScale;
    }

    void TimeRun()
    {
        //Debug.Log("------- TimeRun -------");
        //gameObject.GetComponent<BoxCollider2D>().offset = new Vector2(1, 0);
        Time.timeScale = 1.0f;
        Time.fixedDeltaTime = 0.02F * Time.timeScale;
    }

    void turnTag()
    {
        gameObject.tag = trunTag;
    }

    IEnumerator TurnRight(bool turnRight)
    {
        if (turnRight)
        {
            yield return new WaitForSeconds(2.0f);
            transform.localScale = new Vector3(1.0f, 1.0f, 1.0f);
        }
        else if (!turnRight)
        {
            yield return new WaitForSeconds(2.0f);
            transform.localScale = new Vector3(-1.0f, 1.0f, 1.0f);
        }
    }
}
```
