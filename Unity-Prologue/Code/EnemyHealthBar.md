
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class EnemyLife : MonoBehaviour
{
    public float TESTPOSITION;

    public GameObject Actor;

    public Text healthText;
    public static int HealthCurrent;
    public static int HealthMax;

    private Image healthBar;

    Vector3 HealthPosition, TextPosition;

    void Start()
    {
        healthBar = GetComponent<Image>();
    }
    
    void Update()
    {
        HealthPosition = new Vector3(Actor.transform.position.x, Actor.transform.position.y + 1.88f, transform.position.z);
        transform.position = HealthPosition;

        TextPosition = new Vector3(Actor.transform.position.x, Actor.transform.position.y + 1.88f, transform.position.z);
        healthText.transform.position = TextPosition;

        healthBar.fillAmount = (float)HealthCurrent / (float)HealthMax;
        healthText.text = HealthCurrent.ToString() + "/" + HealthMax.ToString();
    }
}
```
![image](https://user-images.githubusercontent.com/55220866/199516395-f14ab140-8b77-4bf4-b9f4-120b4d1a65bc.png)
![image](https://user-images.githubusercontent.com/55220866/199516491-87accb20-5ea0-429f-8f7a-78d4bbd7a65a.png)
---
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
[.](https://www.youtube.com/watch?v=y7d0naG0ALM)
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
[.](https://github.com/ChengHan16)
