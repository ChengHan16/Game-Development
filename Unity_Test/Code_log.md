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
### 🔸 Coroutine 寫法差異 <br> &emsp;&thinsp;&thinsp; StartCoroutine("MyPrint"); //此方法可以隨時停止Coroutine <br> &emsp;&thinsp;&thinsp; StopCoroutine("MyPrint"); <br> &emsp;&thinsp;&thinsp; StartCoroutine(MyPrint()); //此方法無法停止
## 🔷 C#-類別與物件Class and Object
### `Test.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{

    //C#物件導向程式
    //用程式碼做出虛擬物件
    //也可稱虛擬物件為實體(instance)
    //因為把程式碼寫在Class裡
    //所以Class又稱物件的藍圖

    // Start is called before the first frame update
    void Start()
    {
        MyCharacter _myChar = new MyCharacter();
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
### `MyCharacter.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class MyCharacter
{
    string name;
    int health;
    int speed;

    public MyCharacter()
    {
        name = "hero";
        health = 100;
        speed = 50;
        Debug.Log("初始化了");
    }
}
```
## 🔷 C#-類別與物件Class and Object 自行輸入值
### `Test.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{

    //C#物件導向程式
    //用程式碼做出虛擬物件
    //也可稱虛擬物件為實體(instance)
    //因為把程式碼寫在Class裡
    //所以Class又稱物件的藍圖

    // Start is called before the first frame update
    void Start()
    {
        MyCharacter _myChar = new MyCharacter("player2",510,410);
        _myChar.mystate(); //需要列印結果加上這行

    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
### `MyCharacter.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class MyCharacter
{
    string name;
    int health;
    int speed;

    public MyCharacter(string name,int health,int speed)
    {
        this.name = name;
        this.health = health;
        this.speed = speed;
    }

    public void mystate()
    {
        Debug.Log("初始化了");
        Debug.Log("name = " + name);
        Debug.Log("health = " + health);
        Debug.Log("speed = " + speed);
    }

}
```
## 🔷 C#-繼承Inheritance
### `Test.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        Hero myhero = new Hero();
        myhero.SetMyCharacter("myHero",100,50);
        myhero.mystate();
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
### `Hero.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Hero : MyCharacter //Error:當被繼承時，是不帶有任何參數,
                                //當前Hero已繼承MyCharacter
{

}
```
### `MyCharacter.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class MyCharacter
{
    string name;
    int health;
    int speed;

    public MyCharacter()
    {

    }

    public void SetMyCharacter(string name,int health,int speed)
    {
        this.name = name;
        this.health = health;
        this.speed = speed;
    }

    public void mystate()
    {
        Debug.Log("初始化了");
        Debug.Log("name = " + name);
        Debug.Log("health = " + health);
        Debug.Log("speed = " + speed);
    }

}
```
### 🔸 型別補充 <br> &emsp;&thinsp;&thinsp; public 公開所有都可使用 <br> &emsp;&thinsp;&thinsp; private 私有,其他class不可使用 <br> &emsp;&thinsp;&thinsp; protected 只有繼承者才能使用

## 🔷 C#-繼承Inheritance 1-2
### 🔸 說明：當呼叫 Hero  時會先執行 MyCharacter 內的 myState,再去執行 class Hero 內的程式
### `Test.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        Hero myhero = new Hero();
        myhero.SetMyCharacter("myHero",100,50);
        myhero.mystate();
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
### `Hero.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Hero : MyCharacter
{
    public override void mystate()
    {
        base.mystate();

        Debug.Log("BBBBB");
    }
}
```
### `MyCharacter.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class MyCharacter
{
    public string name;
    private int health;
    protected int speed;

    public MyCharacter()
    {

    }

    public void SetMyCharacter(string name,int health,int speed)
    {
        this.name = name;
        this.health = health;
        this.speed = speed;
    }

    public virtual void mystate()
    {
        Debug.Log("初始化了");
        Debug.Log("name = " + name);
        Debug.Log("health = " + health);
        Debug.Log("speed = " + speed);
    }
}
```
## 🔷 C#-封裝Encapsulation 將物件設為 private ,使用Get讀取資料
### `Test.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        Hero myhero = new Hero();
        //myhero.mystate(); //列印myhero內的mystate資料

        Debug.Log(myhero.GetName()); //指讀取到myhero內的name
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
### `Hero.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Hero : MyCharacter
{
    
}
```
### `MyCharacter.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class MyCharacter
{
    private string name;
    private int health;
    private int speed;

    public MyCharacter()
    {
        name = "MyHero";
        health = 10;
        speed = 1;
    }

    public void SetMyCharacter(string name,int health,int speed)
    {
        this.name = name;
        this.health = health;
        this.speed = speed;
    }

    public string GetName()
    {
        return this.name;
    }

    public int GetHealth()
    {
        return this.health;
    }

    public int Speed()
    {
        return this.speed;
    }

    public virtual void mystate()
    {
        Debug.Log("初始化了");
        Debug.Log("name = " + name);
        Debug.Log("health = " + health);
        Debug.Log("speed = " + speed);
    }
}
```
## 🔷 C# 委託Delegate

## 🔷 GetComponent 基本用法
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    SpriteRenderer mySR;

    // Start is called before the first frame update
    void Start()
    {
        mySR = GetComponent<SpriteRenderer>();
        mySR.color = Color.green;
    }

    // Update is called once per frame
    void Update()
    {
        
    }

}
```
## 🔷 利用其他物件&程式改變另其他物件顏色 (GetComponent
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Car : MonoBehaviour
{
    SpriteRenderer mySR2;
    

    // Start is called before the first frame update
    void Start()
    {
        mySR2 = GameObject.Find("Circle").GetComponent<SpriteRenderer>();
        //若Circle在Main Camera資料下的話要改寫以下
        //mySR2 = GameObject.Find("Main Camera/Circle")

        mySR2.color = Color.blue;
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}
```
## 🔷 判斷按下哪個按鍵 (input
### 🔸 需要在寫在 Update 內
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Car : MonoBehaviour
{
    SpriteRenderer mySR2;
    

    // Start is called before the first frame update
    void Start()
    {
        mySR2 = GameObject.Find("Circle").GetComponent<SpriteRenderer>();
        //若Circle在Main Camera資料下的話要改寫以下
        //mySR2 = GameObject.Find("Main Camera/Circle")

        mySR2.color = Color.blue;
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.LeftArrow))
        {
            Debug.Log("LeftArrow is pressed");
        }
    }
}

```
## 🔷 C# 委託Delegate 
### 🔸 當我按下左方向鍵時會執行 myDelegate 並且是有帶參數的值 Ex.5
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Car : MonoBehaviour
{
    public delegate void MyDelegate(int a);
    public MyDelegate myDelegate;

    // Start is called before the first frame update
    void Start()
    {
        myDelegate += Num1;
        myDelegate += Num2;
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.LeftArrow))
        {
            myDelegate(5);
        }
    }
    
    void Num1(int a)
    {
        Debug.Log("Num1 = " + a);
    }

    void Num2(int a)
    {
        Debug.Log("Num2 = " + a *2);
    }

}
```
## 🔷 C# 委託 Delegate 1-1
### 🔸 與其他程式的 Delegate 做連結
### `Test.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    SpriteRenderer mySR;

    // Start is called before the first frame update
    void Start()
    {
        GameObject.Find("Car").GetComponent<Car>().myDelegate += Num3;
    }

    // Update is called once per frame
    void Update()
    {
        
    }

    void Num3(int a)
    {
        Debug.Log("Num3 = " + a * 3);
    }

}
```
### `Car.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Car : MonoBehaviour
{
    public delegate void MyDelegate(int a);
    public MyDelegate myDelegate;

    // Start is called before the first frame update
    void Start()
    {
        myDelegate += Num1;
        myDelegate += Num2;
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.LeftArrow))
        {
            myDelegate(5);
        }
    }
    
    void Num1(int a)
    {
        Debug.Log("Num1 = " + a);
    }

    void Num2(int a)
    {
        Debug.Log("Num2 = " + a *2);
    }

}
```
## 🔷 C# 委託 Delegate 1-2
### 🔸 通常作法 會將 MyDelegate 設為靜態事件 <br> &emsp;&thinsp;&thinsp; public static event MyDelegate myDelegate; 此方式電腦會為 MyDelegate 做一個實體
### `Test.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour
{
    SpriteRenderer mySR;

    // Start is called before the first frame update
    void Start()
    {
        //GameObject.Find("Car").GetComponent<Car>().myDelegate += Num3;
        Car.myDelegate += Num3;
    }

    // Update is called once per frame
    void Update()
    {
        
    }

    void Num3(int a)
    {
        Debug.Log("Num3 = " + a * 3);
    }

}
```
## `Car.cs`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Car : MonoBehaviour
{
    public delegate void MyDelegate(int a);
    public static event MyDelegate myDelegate;

    // Start is called before the first frame update
    void Start()
    {
        myDelegate += Num1;
        myDelegate += Num2;
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.LeftArrow))
        {
            myDelegate(5);
        }
    }
    
    void Num1(int a)
    {
        Debug.Log("Num1 = " + a);
    }

    void Num2(int a)
    {
        Debug.Log("Num2 = " + a *2);
    }

}
```
---
## `Player`
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour
{

    public float mySpeed;

    void Start()
    {
        
    }

    void Update()
    {
        float a = Input.GetAxis("Horizontal"); 
        if (a > 0)
        {
            transform.localScale = new Vector3(1f, 1f, 1f);
        }
        else if (a < 0)
        {
            transform.localScale = new Vector3(-1f, 1f, 1f);
        }
        float temp = transform.position.x + a * Time.deltaTime * mySpeed;
        transform.position = new Vector3(temp, transform.position.y, transform.position.z);

    }
}
```
### 🔷 `player` 3-6 新增動畫與切換動畫
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour
{

    public float mySpeed;
    Animator myAnim;

    void Start()
    {
        myAnim = GetComponent<Animator>();
    }

    void Update()
    {
        //float a = Input.GetAxis("Horizontal");
        float a = Input.GetAxisRaw("Horizontal");
        if (a > 0)
        {
            transform.localScale = new Vector3(1f, 1f, 1f);
        }
        else if (a < 0)
        {
            transform.localScale = new Vector3(-1f, 1f, 1f);
        }

        myAnim.SetFloat("Run", Mathf.Abs(a));
        float temp = transform.position.x + a * Time.deltaTime * mySpeed;
        transform.position = new Vector3(temp, transform.position.y, transform.position.z);

    }
}
```
## 🔷 p86
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour
{

    public float mySpeed;
    Animator myAnim;

    private void Awake() //程式執行後是第一個被調動的程式
    {
        myAnim = GetComponent<Animator>();
    }

    void Start()
    {
     
    }

    void Update()
    {
        //float a = Input.GetAxis("Horizontal");
        float a = Input.GetAxisRaw("Horizontal");
        if (a > 0)
        {
            transform.localScale = new Vector3(1f, 1f, 1f);
        }
        else if (a < 0)
        {
            transform.localScale = new Vector3(-1f, 1f, 1f);
        }

        myAnim.SetFloat("Run", Mathf.Abs(a));
        float temp = transform.position.x + a * Time.deltaTime * mySpeed;
        transform.position = new Vector3(temp, transform.position.y, transform.position.z);

    }
}
```
## 🔷 p87
### 🔸 產生問題 <br> &emsp;&thinsp; 角色左右時無動畫,上&下才有 <br> &emsp;&thinsp; myAnim.SetFloat("Run", Mathf.Abs(a)); 此段有衝突需用 if 判斷式解決
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour
{

    public float mySpeed;
    Animator myAnim;

    private void Awake() //程式執行後是第一個被調動的程式
    {
        myAnim = GetComponent<Animator>();
    }

    void Start()
    {
     
    }

    void Update()
    {
        float a = Input.GetAxisRaw("Horizontal");
        float b = Input.GetAxisRaw("Vertical");

        if (a > 0)
        {
            transform.localScale = new Vector3(1f, 1f, 1f);
        }
        else if (a < 0)
        {
            transform.localScale = new Vector3(-1f, 1f, 1f);
        }

        myAnim.SetFloat("Run", Mathf.Abs(a));
        myAnim.SetFloat("Run", Mathf.Abs(b));

        float temp = transform.position.x + a * Time.deltaTime * mySpeed;
        float tempY = transform.position.y + b * Time.deltaTime * mySpeed;

        transform.position = new Vector3(temp, tempY, transform.position.z);

    }
}
```
## 🔷 p89,90
### 🔸 解決產生問題 p87
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour
{

    public float mySpeed;
    Animator myAnim;

    private void Awake() //程式執行後是第一個被調動的程式
    {
        myAnim = GetComponent<Animator>();
    }

    void Start()
    {
     
    }

    void Update()
    {
        float a = Input.GetAxisRaw("Horizontal");
        float b = Input.GetAxisRaw("Vertical");

        if (a > 0)
        {
            transform.localScale = new Vector3(1f, 1f, 1f);
        }
        else if (a < 0)
        {
            transform.localScale = new Vector3(-1f, 1f, 1f);
        }

        if (Mathf.Abs(a) > 0.1f && b == 0)
        {
            myAnim.SetFloat("Run", Mathf.Abs(a));
        }
        else if (Mathf.Abs(b) > 0.1f && a == 0)
        {
            myAnim.SetFloat("Run", Mathf.Abs(b));
        }
        else if(Mathf.Abs(a) > 0.1f && Mathf.Abs(b) > 0.1f)
        {
            myAnim.SetFloat("Run", Mathf.Abs(a));
        }
        else
        {
            myAnim.SetFloat("Run", 0);
        }

        float temp = transform.position.x + a * Time.deltaTime * mySpeed;
        float tempY = transform.position.y + b * Time.deltaTime * mySpeed;

        transform.position = new Vector3(temp, tempY, transform.position.z);

    }
}
```
## 🔷 修改 Code 備份
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour
{

    public float mySpeed;
    Animator myAnim;

    private void Awake() //程式執行後是第一個被調動的程式
    {
        myAnim = GetComponent<Animator>();
    }

    void Start()
    {
     
    }

    void Update()
    {
        float a = Input.GetAxisRaw("Horizontal");
        float b = Input.GetAxisRaw("Vertical");

        if (a > 0)
        {
            transform.localScale = new Vector3(1f, 1f, 1f);
        }
        else if (a < 0)
        {
            transform.localScale = new Vector3(-1f, 1f, 1f);
        }

        if (Mathf.Abs(a) > 0.1f && b == 0)
        {
            myAnim.SetFloat("Run", Mathf.Abs(a));
        }
        else if (Mathf.Abs(b) > 0.1f && a == 0)
        {
            myAnim.SetFloat("Run", Mathf.Abs(b));
        }
        else if(Mathf.Abs(a) > 0.1f && Mathf.Abs(b) > 0.1f)
        {
            myAnim.SetFloat("Run", Mathf.Abs(a));
        }
        else
        {
            myAnim.SetFloat("Run", 0);
        }

        float temp = transform.position.x + a * Time.deltaTime * mySpeed;
        float tempY = transform.position.y + b * Time.deltaTime * mySpeed;

        transform.position = new Vector3(temp, tempY, transform.position.z);

    }
}
```

---
# 參考資料
### Unity API
> https://docs.unity3d.com/ScriptReference/SpriteRenderer-color.html
### game art 2d
> https://www.gameart2d.com/
