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
