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

#### Report
------------------------------------------------------------------
#### Title
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




