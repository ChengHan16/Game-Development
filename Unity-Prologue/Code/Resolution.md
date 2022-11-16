### 解析度設定、全螢幕模式選擇、垂直同步、FPS顯示
### [Demo Video](https://youtu.be/VE3Q27oVn48)
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using TMPro;

public class ScreenController : MonoBehaviour
{
    string Res, FSMode; 
    public Toggle FullScreenBtn, VsyncBtn;
    public TextMeshProUGUI ResolutionAndHz, ResolutionText, FullScreenModeText;
    public TMP_Dropdown ddFruites, ResDrop;

    void Start()
    {
        Screen.SetResolution(Screen.currentResolution.width, Screen.currentResolution.height, Screen.fullScreenMode);
        Screen.fullScreen = true;

        if (Screen.fullScreenMode == FullScreenMode.Windowed)
        {
            FullScreenBtn.isOn = false;
        }
        else if (Screen.fullScreenMode == FullScreenMode.FullScreenWindow)
        {
            ddFruites.value = 1;
            FullScreenBtn.isOn = true;
        }

        if (FullScreenBtn.isOn)
        {
            ddFruites.value = 1;
        }
        else if (!FullScreenBtn.isOn)
        {
            ddFruites.value = 1;
        }

        int frameRateCap = 1000;
        Application.targetFrameRate = frameRateCap;
        QualitySettings.vSyncCount = 0;

        if (Screen.currentResolution.width == 1280)
        {
            ResDrop.value = 0;
        }
        else if (Screen.currentResolution.width == 1920)
        {
            ResDrop.value = 1;
        }
        else if (Screen.currentResolution.width == 2560)
        {
            ResDrop.value = 2;
        }
        else if (Screen.currentResolution.width == 3840)
        {
            ResDrop.value = 3;
        }
    }

    private void Update()
    {
        int hz = Screen.currentResolution.refreshRate;

        Res = (Screen.width + "x" + Screen.height + " " + hz + "hz");
        ResolutionAndHz.text = Res;

        FSMode = Screen.fullScreenMode.ToString();
        FullScreenModeText.text = FSMode;

        //Debug.Log(Res); //解析度和刷新率
        //Debug.Log(Screen.fullScreenMode); //螢幕模式
        //Debug.Log(Screen.currentResolution.width + "x" + Screen.currentResolution.height); //當前螢幕長寬
        //Debug.Log(FullScreenBtn.isOn); //全螢幕按鈕布林值
        //Debug.Log(ddFruites.value); //螢幕模式選擇 Value
    }

    public void ChangeFullScreen()
    {
        if (Screen.fullScreenMode == FullScreenMode.ExclusiveFullScreen)
        {
            ddFruites.value = 1;
            FullScreenBtn.isOn = false;
        }
        Screen.fullScreen = !Screen.fullScreen; 

    }

    public void Vsync()
    {
        if (VsyncBtn.isOn)
        {
            QualitySettings.vSyncCount = 1;
        }
        else
        {
            QualitySettings.vSyncCount = 0;
        }
    }

    public void ExitGame()
    {
        Application.Quit();
    }

    //─── Screen.SetResolution ─── [Start]
    public void ChangeResolution(int val)
    {
        if (val == 0)
        {
            Screen.SetResolution(1280, 720, Screen.fullScreenMode);
            ResolutionText.text = "HD";
        }
        if (val == 1)
        {
            //Screen.SetResolution(1280, 720, true);
            Screen.SetResolution(1920, 1080, Screen.fullScreenMode);
            ResolutionText.text = "FHD";
        }
        if (val == 2)
        {
            Screen.SetResolution(2560, 1440, Screen.fullScreenMode);
            ResolutionText.text = "2K";
        }
        if (val == 3)
        {
            Screen.SetResolution(3840, 2160, Screen.fullScreenMode);
            ResolutionText.text = "4K";
        }
    }
    //─── Screen.SetResolution ─── [END]

    public void ScreenMode(int val)
    {
        if (val == 0)
        {
            FullScreenBtn.isOn = true; 
            Screen.SetResolution(Screen.width, Screen.height, FullScreenMode.ExclusiveFullScreen);

        }
        else if (val == 1)
        {
            if (Screen.fullScreenMode == FullScreenMode.FullScreenWindow || Screen.fullScreen)
            {
                FullScreenBtn.isOn = true; 
                Screen.SetResolution(Screen.width, Screen.height, FullScreenMode.FullScreenWindow);
            }
            else
            {
                FullScreenBtn.isOn = false;
                Screen.SetResolution(Screen.width, Screen.height, FullScreenMode.FullScreenWindow);
            }
        }
    }
}
```
### 參考資料：
[Unity Documentation Screen](https://docs.unity3d.com/ScriptReference/Screen.html) <br>
[Unity Documentation Screen.currentResolution](https://docs.unity3d.com/ScriptReference/Screen-currentResolution.html) <br>
[Unity Documentation Screen.SetResolution](https://docs.unity3d.com/ScriptReference/Screen.SetResolution.html) <br>
[How to create an FPS display | Unity Tutorial](https://www.youtube.com/watch?v=xOCScMQIxrU) <br>
[how to see fps? (frames per second)](https://answers.unity.com/questions/1189486/how-to-see-fps-frames-per-second.html) <br>
