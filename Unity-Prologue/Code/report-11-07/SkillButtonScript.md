### SkillButtonScript
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class SkillButtonScript : MonoBehaviour
{
    private Button SkillBtn1, SkillBtn2, SkillBtn3;

    GameObject skillPanel;
    PlayerSkillPanelScript skillScript;

    public float skillTimeCheck, skillUIBar;
    public bool SkillCheckbool, SetSkill1Bar, SetSkill2Bar, SetSkill3Bar;

    private void Awake()
    {
        SkillBtn1 = GameObject.Find("SkillPanelCanvas/PlayerSkillPanel/Skill1").GetComponent<Button>();
        SkillBtn2 = GameObject.Find("SkillPanelCanvas/PlayerSkillPanel/Skill2").GetComponent<Button>();
        SkillBtn3 = GameObject.Find("SkillPanelCanvas/PlayerSkillPanel/Skill3").GetComponent<Button>();
        skillPanel = GameObject.Find("PlayerSkillPanel");
        skillScript = GameObject.Find("SkillPanelCanvas/PlayerSkillPanelScript").GetComponentInParent<PlayerSkillPanelScript>();

        SkillCheckbool = true;
        SetSkill1Bar = false;
        SetSkill2Bar = false;
        SetSkill3Bar = false;

        PlayerSkillUIBar.SkillCurrent = skillUIBar;
    }

    void Start()
    {
        PlayerSkillBar.SkillMax = 10;
        PlayerSkillBar.SkillCurrent = skillTimeCheck;
        PlayerSkill2Bar.SkillMax = 10;
        PlayerSkill2Bar.SkillCurrent = skillTimeCheck;
        PlayerSkill3Bar.SkillMax = 10;
        PlayerSkill3Bar.SkillCurrent = skillTimeCheck;
    }

    void Update()
    {
        if (skillScript.skill >= 1)
        {
            if (Input.GetKeyDown(KeyCode.U))
            {
                FeadToColorSkill1(SkillBtn1.colors.pressedColor);
                FeadToColorSkill2(SkillBtn2.colors.normalColor);
                FeadToColorSkill3(SkillBtn3.colors.normalColor);
                OnSkill1();
            }
            else if (Input.GetKey(KeyCode.U))
            {
                SkillOnCheck();
            }
            else if (Input.GetKeyUp(KeyCode.U)) //skillTimeCheck != 0 && 
            {
                skillTimeCheck = 0.0f;
                resetSkillCurrent();
                SkillCheckbool = true;
            }
        }

        if (skillScript.skill >= 2)
        {
            if (Input.GetKeyDown(KeyCode.I))
            {
                FeadToColorSkill1(SkillBtn1.colors.normalColor);
                FeadToColorSkill2(SkillBtn2.colors.pressedColor);
                FeadToColorSkill3(SkillBtn3.colors.normalColor);
                OnSkill2();
            }
            else if (Input.GetKey(KeyCode.I))
            {
                Skill2OnCheck();
            }
            else if (Input.GetKeyUp(KeyCode.I)) //skillTimeCheck != 0 && 
            {
                skillTimeCheck = 0.0f;
                resetSkillCurrent();
                SkillCheckbool = true;
            }
        }

        if (skillScript.skill >= 3)
        {
            if (Input.GetKeyDown(KeyCode.O))
            {
                FeadToColorSkill1(SkillBtn1.colors.normalColor);
                FeadToColorSkill2(SkillBtn2.colors.normalColor);
                FeadToColorSkill3(SkillBtn3.colors.pressedColor);
                OnSkill3();
            }
            else if (Input.GetKey(KeyCode.O))
            {
                Skill3OnCheck();
            }
            else if (Input.GetKeyUp(KeyCode.O)) //skillTimeCheck != 0 && 
            {
                skillTimeCheck = 0.0f;
                resetSkillCurrent();
                SkillCheckbool = true;
            }
        }
    }

    public void FeadToColorSkill1(Color color)
    {
        if (Input.GetKeyDown(KeyCode.B))
        {
            //color = new Color(0.3f, 0.4f, 0.6f, 0.3f);
            color = new Color(0.2f, 1.0f, 1.0f, 0.8f);
            Graphic graphic = GameObject.Find("SkillPanelCanvas/PlayerSkillPanel/Skill1").GetComponent<Graphic>();
            graphic.CrossFadeColor(color, SkillBtn1.colors.fadeDuration, true, true);

            //skill1check = 1;
        }
        else{
            color = new Color(1.0f, 1.0f, 1.0f, 1.0f);
            Graphic graphic = GameObject.Find("SkillPanelCanvas/PlayerSkillPanel/Skill1").GetComponent<Graphic>();
            graphic.CrossFadeColor(color, SkillBtn1.colors.fadeDuration, true, true);
        }
    }
    void FeadToColorSkill2(Color color)
    {
        if (Input.GetKeyDown(KeyCode.N))
        {
            color = new Color(0.2f, 0.2f, 1.0f, 0.8f);
            Graphic graphic = GameObject.Find("SkillPanelCanvas/PlayerSkillPanel/Skill2").GetComponent<Graphic>();
            graphic.CrossFadeColor(color, SkillBtn2.colors.fadeDuration, true, true);
        }
        else
        {
            color = new Color(1.0f, 1.0f, 1.0f, 1.0f);
            Graphic graphic = GameObject.Find("SkillPanelCanvas/PlayerSkillPanel/Skill2").GetComponent<Graphic>();
            graphic.CrossFadeColor(color, SkillBtn2.colors.fadeDuration, true, true);
        }
    }
    void FeadToColorSkill3(Color color)
    {
        if (Input.GetKeyDown(KeyCode.M))
        {
            color = new Color(1.0f, 0.2f, 0.2f, 0.8f);
            Graphic graphic = GameObject.Find("SkillPanelCanvas/PlayerSkillPanel/Skill3").GetComponent<Graphic>();
            graphic.CrossFadeColor(color, SkillBtn3.colors.fadeDuration, true, true);
        }
        else
        {
            color = new Color(1.0f, 1.0f, 1.0f, 1.0f);
            Graphic graphic = GameObject.Find("SkillPanelCanvas/PlayerSkillPanel/Skill3").GetComponent<Graphic>();
            graphic.CrossFadeColor(color, SkillBtn3.colors.fadeDuration, true, true);
        }
    }

    public void OnSkill1()
    {
        SkillBtn1.onClick.Invoke();
        //Debug.Log("Skill1--- On");
    }

    public void OnSkill2()
    {
        SkillBtn2.onClick.Invoke();
        //Debug.Log("Skill2 --- On");
    }

    public void OnSkill3()
    {
        SkillBtn3.onClick.Invoke();
        //Debug.Log("Skill3 --- On");
    }

    void SkillOnCheck()
    {
        if (skillUIBar >= 60)
        {
            if (SkillCheckbool && skillTimeCheck < 10)
            {
                skillTimeCheck = skillTimeCheck + 0.2f;
                PlayerSkillBar.SkillCurrent = skillTimeCheck;
                SkillCheckbool = false;
                StartCoroutine("IESkillOnCheck");
            }
            else
            {
                return;
            }

            if (skillTimeCheck > 10)
            {
                SetSkill1Bar = true;

            }
            skillPanelOff();
        }
        else
        {
            StartCoroutine("resetCancelskill1");
            return;
        }
    }

    void Skill2OnCheck()
    {
        if (skillUIBar >= 40)
        {
            if (SkillCheckbool && skillTimeCheck < 10)
            {
                skillTimeCheck = skillTimeCheck + 0.2f;
                PlayerSkill2Bar.SkillCurrent = skillTimeCheck;
                SkillCheckbool = false;
                StartCoroutine("IESkillOnCheck");
            }
            else
            {
                return;
            }
            if (skillTimeCheck > 10)
            {
                SetSkill2Bar = true;

            }
            skillPanelOff();
        }
        else
        {
            StartCoroutine("resetCancelskill2");
            return;
        }
    }

    void Skill3OnCheck()
    {
        if (skillUIBar >= 80)
        {
            if (SkillCheckbool && skillTimeCheck < 10)
            {
                skillTimeCheck = skillTimeCheck + 0.2f;
                PlayerSkill3Bar.SkillCurrent = skillTimeCheck;
                SkillCheckbool = false;
                StartCoroutine("IESkillOnCheck");
            }
            else
            {
                return;
            }
            if (skillTimeCheck > 10)
            {
                SetSkill3Bar = true;

            }
            skillPanelOff();
        }
        else
        {
            StartCoroutine("resetCancelskill3");
            return;
        }
    }

    void skillPanelOff()
    {
        if (skillTimeCheck > 10)
        {
            skillPanel.SetActive(false);
            Time.timeScale = 1.0f;
            resetSkillCurrent();
        }
    }

    void resetSkillCurrent()
    {
        PlayerSkillBar.SkillCurrent = 0;
        PlayerSkill2Bar.SkillCurrent = 0;
        PlayerSkill3Bar.SkillCurrent = 0;
    }

    IEnumerator IESkillOnCheck()
    {
        yield return new WaitForSecondsRealtime(0.02f);
        SkillCheckbool = true;
    }

    IEnumerator resetCancelskill1()
    {
        yield return new WaitForSecondsRealtime(0.2f);
        //Debug.Log("No On Click");
        FeadToColorSkill1(SkillBtn1.colors.normalColor);
    }

    IEnumerator resetCancelskill2()
    {
        yield return new WaitForSecondsRealtime(0.2f);
        //Debug.Log("No On Click");
        FeadToColorSkill2(SkillBtn2.colors.normalColor);
    }

    IEnumerator resetCancelskill3()
    {
        yield return new WaitForSecondsRealtime(0.2f);
        //Debug.Log("No On Click");
        FeadToColorSkill3(SkillBtn3.colors.normalColor);
    }
}
```
### PlayerAttactCollider
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class AttactCollider : MonoBehaviour
{
    public string newForm1Tag, newForm2Tag, newForm3Tag, trunTag;
    public Text TagText;

    Player playerScript;
    SkillButtonScript skillScript;

    private void Awake()
    {
        playerScript = Player.FindObjectOfType<Player>();
        skillScript = GameObject.Find("SkillPanelCanvas/PlayerSkillPanel/Skill1/Skill1Script").GetComponentInParent<SkillButtonScript>();
    }

    private void Start()
    {
        gameObject.tag = "PlayerAttact";
        StartCoroutine("reset");
    }

    private void Update()
    {
        //Debug.Log(gameObject.tag);

        if (playerScript.changeType == 1)
        {
            gameObject.tag = newForm1Tag;
            TagText.text = newForm1Tag;
        }
        else if (playerScript.changeType == 2)
        {
            gameObject.tag = newForm2Tag;
            TagText.text = newForm2Tag;
        }
        else if (playerScript.changeType == 3)
        {
            gameObject.tag = newForm3Tag;
            TagText.text = newForm3Tag;
        }
    }

    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (playerScript.changeType == 0 && skillScript.skillUIBar < 100)
        {
            if (collision.tag == "Enemy")
            {
                skillScript.skillUIBar += 50.85f;
                PlayerSkillUIBar.SkillCurrent = skillScript.skillUIBar;
            }
        }

        if (playerScript.changeType == 1 && skillScript.skillUIBar < 100)
        {
            if (collision.tag == "Enemy")
            {
                skillScript.skillUIBar += 10.5f;
                PlayerSkillUIBar.SkillCurrent = skillScript.skillUIBar;
            }
        }

        if (playerScript.changeType == 2 && skillScript.skillUIBar < 100)
        {
            if (collision.tag == "Enemy")
            {
                skillScript.skillUIBar += 15.5f;
                PlayerSkillUIBar.SkillCurrent = skillScript.skillUIBar;
            }
        }

        if (playerScript.changeType == 3)
        {
            if (collision.tag == "Enemy")
            {
                skillScript.skillUIBar += 18.5f;
                PlayerSkillUIBar.SkillCurrent = skillScript.skillUIBar;
            }
        }
    }

    IEnumerator reset()
    {
        yield return new WaitForSeconds(0.01f);
        this.gameObject.SetActive(false);
    }
}
```
### PlayerSkillUIBar
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class PlayerSkillUIBar : MonoBehaviour
{
    public static float SkillCurrent;
    public static float SkillMax;
    public float SkillTimer;

    private Image SkillBar;

    SkillButtonScript skillScript;
    bool DelaySkill;

    private void Awake()
    {
        SkillBar = GetComponent<Image>();
        skillScript = GameObject.Find("SkillPanelCanvas/PlayerSkillPanel/Skill1/Skill1Script").GetComponentInParent<SkillButtonScript>();

        DelaySkill = true;
    }

    private void Start()
    {
        SkillMax = 100;

        SkillTimer = 0;
    }

    void Update()
    {
        //Debug.Log("SkillTimer : " + SkillTimer);
        //Debug.Log("skillScript.SetSkill1Bar : " + skillScript.SetSkill1Bar);

        SkillBar.fillAmount = (float)SkillCurrent / (float)SkillMax;

        if (skillScript.SetSkill1Bar && DelaySkill)
        {
            if (SkillTimer < 60)
            {
                DelaySkill = false;
                SkillTimer += 1;

                Player.FindObjectOfType<Player>().changeType = 1;
                skillScript.skillUIBar = skillScript.skillUIBar - 1.0f;
                SkillCurrent = skillScript.skillUIBar;

                StartCoroutine("DelayShort");

                if (SkillTimer >= 60)
                {
                    SkillTimer = 0;
                    skillScript.SetSkill1Bar = false;
                }
            }
        }

        if (skillScript.SetSkill2Bar && DelaySkill)
        {
            if (SkillTimer < 40)
            {
                DelaySkill = false;
                SkillTimer += 1;

                Player.FindObjectOfType<Player>().changeType = 2;
                skillScript.skillUIBar = skillScript.skillUIBar - 1.0f;
                SkillCurrent = skillScript.skillUIBar;

                StartCoroutine("DelayShort");

                if (SkillTimer >= 40)
                {
                    SkillTimer = 0;
                    skillScript.SetSkill2Bar = false;
                }
            }
        }

        if (skillScript.SetSkill3Bar && DelaySkill)
        {
            if (SkillTimer < 80)
            {
                DelaySkill = false;
                SkillTimer += 1;

                Player.FindObjectOfType<Player>().changeType = 3;
                skillScript.skillUIBar = skillScript.skillUIBar - 1.0f;
                SkillCurrent = skillScript.skillUIBar;

                StartCoroutine("DelayShort");

                if (SkillTimer >= 80)
                {
                    SkillTimer = 0;
                    skillScript.SetSkill3Bar = false;
                }
            }
        }
    }

    IEnumerator DelayShort()
    {
        yield return new WaitForSecondsRealtime(0.001f);
        DelaySkill = true;
    }
}
```
## ────────── SKILL END ──────────
