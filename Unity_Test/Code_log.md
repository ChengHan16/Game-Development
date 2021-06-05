```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        //Calculation();
        Calculation2(5,6);
        int ff = Calculation();
    }

    // Update is called once per frame
    void Update()
    {
        
    }

    void Calculation2(int a,int b) //有參數的副函式
    {
        int c = a + b;
        Debug.Log("Calculation2_a+b：" + c);
    }

    int Calculation() {
    int a = 2;
    int b = 3;
    int c = a + b;
    //Debug.Log("a+b：" + c);
        return c;
    }

}

```
