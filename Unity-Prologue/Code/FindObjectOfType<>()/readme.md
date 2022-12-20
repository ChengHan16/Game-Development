### 使用 foreach loop 抓取預設物件腳本 **用於多個物件 PreFab**

### 關鍵
```C#
using System.Linq;
Sign[] myDialogue;

var ss = FindObjectsOfType<腳本名稱>().OfType<腳本名稱>();
foreach (腳本名稱 s in ss) {
     ss = myDialogue;
     Debug.Log("Object：" + s);
}
```
------
```C#
var ss = FindObjectsOfType<Sign>().OfType<Sign>();

foreach (Sign s in ss)
{
    ss = myDialogue;
    Debug.Log("出自CameraController腳本,抓取物多個件腳本"+":"+ "\n" +"Object："+ s);

    if (s.setCameraPosi)
    {
        ScreenX = ScreenXValue;
        if (ScreenXValue > 0.3f)
        {
            StartCoroutine(RightWaitAdd());
        }
        GetComponent<CinemachineVirtualCamera>().GetCinemachineComponent<CinemachineFramingTransposer>().m_ScreenX = ScreenX;
     }
}
```
-------
### 參考資料：
### [How can I find all objects that have a script that implements a certain interface?](https://answers.unity.com/questions/863509/how-can-i-find-all-objects-that-have-a-script-that.html)
