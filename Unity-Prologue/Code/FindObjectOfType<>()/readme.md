### 使用 foreach loop 抓取預設物件腳本 **用於多個物件 PreFab**
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
