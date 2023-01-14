### 2023-01-05 I5302 10:00

![PROLOGUE_DOWNLOAD](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Download_Img.png?raw=true,https://drive.google.com/drive/folders/12fk_TZRc2ip2G5pheyhCnR_cPJU4b605?usp=sharing)

### ≖‿≖  Ending
------------------------
### ● Actor Value Setting

|Actor Name|➹ Attact Value|✚ Life Value|
|---|---|---|
|Common Enemy|25|5 ~ 20|
|Shadow Assassin|50|5 ~ 8|
|Dark side|169|1000|

------------------------
### ● Player get hurt (Collision Enemy Tags) || *For Script：Player [OnTriggerEnter2D]*

|Tag|Hurt Value|
|---|---|
|Enemy|10|
|CommonEnemyAttact|35|
|ShadowAssassinAttact|65|
|DarkSideAttact|95|

------------------------
### ● 場景完成進度

- [x] 主頁面
- [x] 設定面板
- [x] 關卡選擇頁面
------------------------
- [x] 第一章【基本操作】*(Player.Transter.Position = -3.0f, 0.5f, 0f)*
  - [x] 地圖佈置
  - [x] 控制教學提示
  - [x] 敵人
  - [x] 通關條件

|Player ✚Life|Skill State|
|---|---|
|100|Not to|

------------------------
- [x] 第二章【技能操作】
  - [x] 地圖佈置
  - [x] 控制教學提示
  - [x] 敵人
  - [x] 通關條件

|Player ✚Life|Skill State|
|---|---|
|250|Not to|

------------------------
- [x] 第三章【基本關卡】
  - [x] 地圖佈置
  - [x] 敵人
  - [x] 教學內容
  - [x] 通關條件

|Player ✚Life|Skill State|
|---|---|
|250|Not to|

------------------------
- [x] 第四章【王關】
  - [x] 地圖佈置
  - [x] 敵人
  - [x] 教學內容
  - [x] 通關條件

|Player ✚Life|Skill State|
|---|---|
|1000|fully open|

------------------------
- [x] 過關頁面
- [x] 玩家變身圖片
- [x] 玩家變身數值
- [x] 玩家型態攻擊範圍
- [ ] 音樂、音效
------------------------
### ● 需繳交資料
- [x] 報告
- [x] 影片 (待審核)
- [x] 海報
<br>

*--------------------------------------------------------------------------- END ---------------------------------------------------------------------------*

<br>
<br>
<br>
<br>
<br>
<br>

## Other
---
### 叫出 Console 
按下：Ctrl + Shift + C
------------------------
### Credit (creative arts)
------------------------
### ???
Unity 2D Game Why use a graphics card 3D
[]()

### [Cinemachine_Camera](https://github.com/ChengHan16/Game-Development/tree/main/Unity-Prologue/Code/Cinemachine_Camera)

```
連續移動的輸入除了GetKey / GetButton，也可以使用GetAxis取得X或Y軸數據來設置。

有GetAxis還有GetAxisRaw差別在於

GetAxis回傳-1到1之間的浮點數，例如0.4。

GetAxisRaw只回傳-1、0、1。
```
[unity使用者輸入(GetKey與GetButton)](https://ithelp.ithome.com.tw/m/articles/10263073)

### Unity Method of use
[Scroll Rect](https://docs.unity3d.com/Packages/com.unity.ugui@1.0/manual/script-ScrollRect.html)

### Development Method
[Unity中對UGUI的Image進行傾斜變形](https://blog.csdn.net/linxinfa/article/details/123378696)

[Creating a Custom Tab System in Unity](https://www.youtube.com/watch?v=211t6r12XPQ)

[START MENU in Unity](https://www.youtube.com/watch?v=zc8ac_qUXQY)

[How to make a LOADING BAR in Unity](https://www.youtube.com/watch?v=YMj2qPq9CP8)
------------------------
### [遊戲內容英文類別表達名稱](https://www.zhihu.com/question/325164094)
關卡`Level`
Episode，Chapter章節，Mission任務

### PlayerSkill
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

    public Gradient gradient;

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

        if (SkillCurrent >= 100f)
        {
            SkillBar.color = gradient.Evaluate(1.0f);
        }
        else if (SkillCurrent >= 60)
        {
            SkillBar.color = gradient.Evaluate(0.6f);
        }
        else if (SkillCurrent >= 40f)
        {
            SkillBar.color = gradient.Evaluate(0.4f);
        }


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
