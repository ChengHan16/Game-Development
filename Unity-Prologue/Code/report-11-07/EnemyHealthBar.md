### EnemyLife
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

    EnemyTEST myEnemyScript;

    private void Awake()
    {
        myEnemyScript = GetComponentInParent<EnemyTEST>();
    }

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

        if (myEnemyScript.enemyLife == 0)
        {
            healthText.color = new Color(healthText.color.r, healthText.color.g, healthText.color.b, 0.0f);
        }
    }
}
```
https://www.youtube.com/watch?v=y7d0naG0ALM
