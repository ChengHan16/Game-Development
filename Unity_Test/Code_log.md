# 🔹 首頁
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
## 🔹 有參數&回傳的函式
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
        //Calculation2(5,6);
        //int ff = Calculation();
        //int abc = 5;
        //int def = ff + abc;
        //Debug.Log(def);
        int hh = Calculation2(5,7);
        int edy = 5;
        int ggg = hh + edy;
        Debug.Log(ggg);
    }

    // Update is called once per frame
    void Update()
    {
        
    }

    public int Calculation2(int a,int b) //有參數的副函式
    {
        int c = a + b;
        return c;
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
## 🔹 If, else, &&, || 多判斷
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        int a = 11;
        bool b = true;
        int c = 2;

        // >
        // <
        // >=
        // <=
        // ==
        // !=
        // || 或者,其中一個成立就會執行
        // && 而且,要符合條件才會執行
        
        if(a == 10 && b == true || c ==1)
        {
            Debug.Log("YEAH");
        }

        /*if (a > 10)
        {
            Debug.Log("a>10");
        }
        else if(a > 5)
        {
            Debug.Log("a>5");
        }
        else
        {
            Debug.Log("a<=5");
        }*/
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}

```
## 🔹 switch 判斷 (數值)
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        int a = 2;

        switch (a)
        {
            case 1:
                Debug.Log("a 在預設條件內 a =" + a);
                break; //break意思,執行完就不會繼續執行,就停止

            case 5:
                Debug.Log("a 在預設條件內 a =" + a);
                break;

            case 100:
                Debug.Log("a 在預設條件內 a =" + a);
                break;

            default:
                Debug.Log("a 不在預設條件內 a =" + a);
                break;
        }
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔹 switch 判斷 (字串)
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        string a = "hello";

        switch (a)
        {
            case "hello":
                Debug.Log("a 在預設條件內 a =" + a);
                break; //break意思,執行完就不會繼續執行,就停止

            case "ketty":
                Debug.Log("a 在預設條件內 a =" + a);
                break;

            case "boy":
                Debug.Log("a 在預設條件內 a =" + a);
                break;

            default:
                Debug.Log("a 不在預設條件內 a =" + a);
                break;
        }
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔹 C# array 陣列 1-1
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{

    string[] mystring = new string[3] { "boy", "girl", "YEAH" };
    //string[] mystring = new string[] { "boy", "girl", "YEAH" };

    // Start is called before the first frame update
    void Start()
    {
        /*
         string a = mystring[0]; //mystring第0個位置的字串放到a裡
         Debug.Log(a);
        */

        Debug.Log(mystring[1]);
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔹 C# array 陣列 1-1 2方法
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{

    string[] mystring = new string[3];

    // Start is called before the first frame update
    void Start()
    {
        mystring[0] = "boy";
        mystring[1] = "girl";
        mystring[2] = "YEAH";

        Debug.Log(mystring[2]);
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔹 C# array 陣列 1-2
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{

    string[] mystring = new string[3];

    // Start is called before the first frame update
    void Start()
    {
        mystring[0] = "boy";
        mystring[1] = "girl";
        mystring[2] = "YEAH";

        Debug.Log("第一次給值：mystring[0] = " + mystring[0]);
        Debug.Log("第一次給值：mystring[0] = " + mystring[1]);
        Debug.Log("第一次給值：mystring[0] = " + mystring[2]);

        mystring[0] = "man";
        mystring[1] = "woman";
        mystring[2] = "yes";

        Debug.Log("第一次給值：mystring[0] = " + mystring[0]);
        Debug.Log("第一次給值：mystring[0] = " + mystring[1]);
        Debug.Log("第一次給值：mystring[0] = " + mystring[2]);
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔹 C# array 查看陣列內有多少資料
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{

    string[] mystring = new string[3];

    // Start is called before the first frame update
    void Start()
    {
        mystring[0] = "boy";
        mystring[1] = "girl";
        mystring[2] = "YEAH";

        /*
        int a = mystring.Length;
        Debug.Log(a);
        */
        
        Debug.Log(mystring.Length);
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔹 Unity 特有 C# array 陣列使用
### 🔸 創建 public string[] mystring2; 後在 Inspector 所屬物件程式套件內有 mystring2 選項, <br> &emsp;&thinsp; size為陣列數,點選後可自行輸入值
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{

    string[] mystring = new string[3];
    public string[] mystring2;

    // Start is called before the first frame update
    void Start()
    {
        Debug.Log(mystring2[0]);
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔹 C# List 清單
### 🔸 陣列不可改變內有幾個值，List 可以
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    public List<int> myList = new List<int>() { 8,2,3,2,6 };

    // Start is called before the first frame update
    void Start()
    {
        Debug.Log(myList[0]);
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔹 C# List 清單 加值 .add
### 🔸 執行後 List 加入所 .add 的值
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    public List<int> myList = new List<int>() { 8,2,3,2,6 };

    // Start is called before the first frame update
    void Start()
    {
        myList.Add(9);
        Debug.Log(myList[0]);
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔹 C# 在 List 中選取位置插入值
### 🔸 myList.Insert(插入位置,增加值);
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    public List<int> myList = new List<int>() { 8,2,3,2,6 };

    // Start is called before the first frame update
    void Start()
    {
        myList.Insert(2,99);
        Debug.Log(myList[0]);
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔷 C# 在 List 中移除指定位置的值
### 🔸 myList.RemoveAt(移除位置);
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    public List<int> myList = new List<int>() { 8,2,3,2,6 };

    // Start is called before the first frame update
    void Start()
    {
        myList.RemoveAt(2);
        Debug.Log(myList[0]);
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
### ⚠ RemoveAt & Remove 不同處 <br> &emsp;&thinsp;&thinsp; Remove 會從 List 將第一個 2 刪除掉,而後相同的2不會被刪除
## 🔷 C# 判斷 List 有無特定數值
### 🔸 bool b = myList.Contains(88); //執行後就會尋找有無88,Contains是一個布林值
```C# 
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    public List<int> myList = new List<int>() { 8,2,3,2,6 };

    // Start is called before the first frame update
    void Start()
    {
        bool b = myList.Contains(88); //執行後就會尋找有無88,Contains是一個布林值
        Debug.Log(b);
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔷 C# 判斷 List 內有多少值
### 🔸 int a = myList.Count;
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    public List<int> myList = new List<int>() { 8,2,3,2,6 };

    // Start is called before the first frame update
    void Start()
    {
        int a = myList.Count;
        Debug.Log(a);
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔷 C# 將 List 內值清除
### 🔸 myList.Clear();
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    public List<int> myList = new List<int>() { 8,2,3,2,6 };

    // Start is called before the first frame update
    void Start()
    {
        myList.Clear();
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔷 C# for 迴圈
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    
    // Start is called before the first frame update
    void Start()
    {
        for (int a = 0; a<5; a++)
        {
            Debug.Log("列印第"+ a + "次結果" + a);
        }
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔷 C# 使用 for 迴圈給陣列值 1-1
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{

    int[] myInt = new int[3];
    // Start is called before the first frame update
    void Start()
    {
        for (int i = 0; i<3; i++)
        {
            myInt[i] = i + 1;
            Debug.Log(myInt[i]);
        }
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔷 C# 使用 for 迴圈給陣列值 1-2
### 🔸 for (int i = 0; i<myInt.Length; i++), 比較大小使用.Length 是一樣結果,抓取上方 int[] myInt = new int[5];
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{

    int[] myInt = new int[5];
    // Start is called before the first frame update
    void Start()
    {
        for (int i = 0; i<myInt.Length; i++)
        {
            myInt[i] = i + 1;
            Debug.Log(myInt[i]);
        }
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔷 C# while 迴圈
### 🔸 最後記得設定跳出程式的條件
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{

    bool mybool = true;

    // Start is called before the first frame update
    void Start()
    {
        while (mybool == true)
        {
            Debug.Log("mybool = true");
            mybool = false;
            //最後記得設定跳出程式的條件
        }
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔷 C# 使用 while 迴圈 運作與 for 迴圈一樣的方法 
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{

    int[] myInt = new int[3];

    // Start is called before the first frame update
    void Start()
    {
        int a = 0;
        while (a < 3 )
        {
            myInt[a] = a + 1;
            Debug.Log(myInt[a]);
            a++;
            //最後記得設定跳出程式的條件
        }
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔷 C#-Coroutines協程 (延後程式碼的執行)
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{

    // Start is called before the first frame update
    void Start()
    {
        //Debug.Log("YEAH");
        StartCoroutine("MyPrint");
    }

    IEnumerator MyPrint()
    {
        yield return new WaitForSeconds(2f);
        Debug.Log("YEAH");
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔷 C#-Coroutines協程 (延後程式碼的執行) 多個
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{

    // Start is called before the first frame update
    void Start()
    {
        Debug.Log("馬上列印");
        StartCoroutine("MyPrint");
    }

    IEnumerator MyPrint()
    {
        yield return new WaitForSeconds(2f);
        Debug.Log("等待兩秒");

        yield return new WaitForSeconds(2f);
        Debug.Log("等待四秒");

        yield return new WaitForSeconds(2f);
        Debug.Log("等待六秒");
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
