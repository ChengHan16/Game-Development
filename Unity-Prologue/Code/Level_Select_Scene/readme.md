### [Demo_Video](https://youtu.be/hCs3HXasefU)
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using TMPro;
using UnityEngine.SceneManagement;

public class SelectSenceButtonScript : MonoBehaviour
{
    public TextMeshProUGUI DisplayButton;
    public Sprite buttonSprite;
    //public GameObject Level1Img, Level2Img;
    public GameObject[] myImage;

    Image imageBtn1, imageBtn2, imageBtn3;

    int clearedLevel;

    private void Awake()
    {
        imageBtn1 = GameObject.Find("UICanvas/SelectPanelBGImage/LevelList/Panel/Leve1Button").GetComponent<Image>();
        imageBtn2 = GameObject.Find("UICanvas/SelectPanelBGImage/LevelList/Panel/Leve2Button").GetComponent<Image>();
        imageBtn3 = GameObject.Find("UICanvas/SelectPanelBGImage/LevelList/Panel/Leve3Button").GetComponent<Image>();

        clearedLevel = PlayerPrefs.GetInt("clearedLevel");
        clearedLevel = 2;

        if (clearedLevel == 0)
        {
            imageBtn1.sprite = buttonSprite;
        }
        else if(clearedLevel <= 1)
        {
            imageBtn1.sprite = buttonSprite;
            imageBtn2.sprite = buttonSprite;
        }
        else if (clearedLevel >=2)
        {
            imageBtn1.sprite = buttonSprite;
            imageBtn2.sprite = buttonSprite;
            imageBtn3.sprite = buttonSprite;
        }
    }

    public void GoToMainMenu()
    {
        //SceneManager.LoadScene("MainMenu");
        BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
        myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);

        FadeInOut.instance.SceneFadeInOut("MainMenu");
    }

    public void StartBtn()
    {
        SceneManager.LoadScene("Level" + PlayerPrefs.GetInt("Level"));
        /*Debug.Log("Level" + PlayerPrefs.GetInt("Level"));
        string LevelName = ("Level" + PlayerPrefs.GetInt("Level")).ToString();
        FadeInOut.instance.SceneFadeInOut(LevelName);*/
    }

    public void GoToLevel1()
    {
        //Animator myAnim2 = Level2Img.GetComponent<Animator>();
        //myAnim2.SetTrigger("Level2Dis");
        //Level2Img.SetActive(false);

        myImage[1].SetActive(false);
        
        myImage[0].SetActive(true);

        DisplayButton.text = "Level1";
        string temp = DisplayButton.text.Substring(5);
        int levelNumber = int.Parse(temp);
        PlayerPrefs.SetInt("Level", levelNumber);

        //SceneManager.LoadScene("Level1");
        BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
        myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);

        //FadeInOut.instance.SceneFadeInOut("Level1");
    }

    public void GoToLevel2()
    {
        /*Animator myAnim1 = Level1Img.GetComponent<Animator>();
        myAnim1.SetTrigger("Level1DIs");
        Level1Img.SetActive(false);*/

        if (clearedLevel >= 1)
        {
            myImage[0].SetActive(false);
            myImage[1].SetActive(true);

            DisplayButton.text = "Level2";
            string temp = DisplayButton.text.Substring(5);
            int levelNumber = int.Parse(temp);
            PlayerPrefs.SetInt("Level", levelNumber);

            //SceneManager.LoadScene("Level2");
            BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
            myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);

            //FadeInOut.instance.SceneFadeInOut("Level2");
        }
        else
        {
            BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
            myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[1]);
        }
    }

    public void GoToLevel3()
    {
        if (clearedLevel >=2)
        {
            BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
            myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);

            //SceneManager.LoadScene("Level3");
            FadeInOut.instance.SceneFadeInOut("Level3");
        }
        else
        {
            BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
            myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[1]);
        }
    }
}
```
![image](https://user-images.githubusercontent.com/55220866/206216805-5a9b64d4-f13d-4645-9e60-a26758bf1910.png)

### 正式版
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using TMPro;
using UnityEngine.SceneManagement;

public class SelectSenceButtonScript : MonoBehaviour
{
    public TextMeshProUGUI DisplayButton, directionsText;
    public Sprite buttonSprite;
    //public GameObject Level1Img, Level2Img;
    public GameObject[] myImage, lockedButton;
    public Image[] lockedImage;
    public GameObject OnStartBtn, OnDirectionPanel;
    public string[] Directions;

    Image imageBtn1, imageBtn2, imageBtn3, imageBtn4;
    RectTransform SelectedBtn;

    int clearedLevel;

    private void Awake()
    {
        SelectedBtn = GameObject.Find("UICanvas/SelectPanelBGImage/LevelList/Panel/SelectedBtn").GetComponent<RectTransform>();

        imageBtn1 = GameObject.Find("UICanvas/SelectPanelBGImage/LevelList/Panel/Leve1Button").GetComponent<Image>();
        imageBtn2 = GameObject.Find("UICanvas/SelectPanelBGImage/LevelList/Panel/Leve2Button").GetComponent<Image>();
        imageBtn3 = GameObject.Find("UICanvas/SelectPanelBGImage/LevelList/Panel/Leve3Button").GetComponent<Image>();
        imageBtn4 = GameObject.Find("UICanvas/SelectPanelBGImage/LevelList/Panel/Leve4Button").GetComponent<Image>();

        clearedLevel = PlayerPrefs.GetInt("clearedLevel");
        //clearedLevel = 3;//測試用記得刪除

        if (clearedLevel == 0)
        {
            imageBtn1.sprite = buttonSprite;

            lockedButton[0].SetActive(false);

            lockedImage[0].color = new Color(255f, 255f, 255f, 1);
        }
        else if(clearedLevel <= 1)
        {
            imageBtn1.sprite = buttonSprite;
            imageBtn2.sprite = buttonSprite;

            lockedButton[0].SetActive(false);
            lockedButton[1].SetActive(false);

            lockedImage[0].color = new Color(255f, 255f, 255f, 1);
            lockedImage[1].color = new Color(255f, 255f, 255f, 1);
        }
        else if (clearedLevel >= 2)
        {
            imageBtn1.sprite = buttonSprite;
            imageBtn2.sprite = buttonSprite;
            imageBtn3.sprite = buttonSprite;

            lockedButton[0].SetActive(false);
            lockedButton[1].SetActive(false);
            lockedButton[2].SetActive(false);

            lockedImage[0].color = new Color(255f, 255f, 255f, 1);
            lockedImage[1].color = new Color(255f, 255f, 255f, 1);
            lockedImage[2].color = new Color(255f, 255f, 255f, 1);
        }
        if (clearedLevel >= 3)
        {
            imageBtn1.sprite = buttonSprite;
            imageBtn2.sprite = buttonSprite;
            imageBtn3.sprite = buttonSprite;
            imageBtn4.sprite = buttonSprite;

            foreach (GameObject value in lockedButton)
            {
                //print(value);
                value.SetActive(false);
            }

            foreach (Image value in lockedImage)
            {
                value.color = new Color(255f, 255f, 255f, 1);
            }
        }
    }

    public void GoToMainMenu()
    {
        //SceneManager.LoadScene("MainMenu");
        BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
        myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);

        FadeInOut.instance.SceneFadeInOut("MainMenu");
    }

    public void StartBtn()
    {
        SceneManager.LoadScene("Level" + PlayerPrefs.GetInt("Level")); //Select Sence測試使用

        /*string LevelName = ("Level" + PlayerPrefs.GetInt("Level")).ToString();
        FadeInOut.instance.SceneFadeInOut(LevelName);*/
    }

    public void GoToLevel1()
    {
        DisplayButton.text = "Level1";
        SelectButtonOn();

        SelectedBtn.anchoredPosition = new Vector2(0f, 1747f);
        SelectedBtn.localScale = new Vector2(1f, 1f);

        myImage[1].SetActive(false); 
        myImage[2].SetActive(false);
        myImage[3].SetActive(false);
        myImage[0].SetActive(true);

        BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
        myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);
        //SceneManager.LoadScene("Level1");
        //FadeInOut.instance.SceneFadeInOut("Level1");
    }

    public void GoToLevel2()
    {
        if (clearedLevel >= 1)
        {
            DisplayButton.text = "Level2";
            SelectButtonOn();

            SelectedBtn.anchoredPosition = new Vector2(0f, 1167f);
            SelectedBtn.localScale = new Vector2(-1f, 1f);

            myImage[0].SetActive(false);
            myImage[2].SetActive(false);
            myImage[3].SetActive(false);
            myImage[1].SetActive(true);

            BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
            myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);
            //SceneManager.LoadScene("Level2");
            //FadeInOut.instance.SceneFadeInOut("Level2");
        }
        else
        {
            BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
            myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[1]);
        }
    }

    public void GoToLevel3()
    {
        if (clearedLevel >=2)
        {
            DisplayButton.text = "Level3";
            SelectButtonOn();

            SelectedBtn.anchoredPosition = new Vector2(0f, 587f);
            SelectedBtn.localScale = new Vector2(1f, 1f);

            myImage[0].SetActive(false);
            myImage[1].SetActive(false);
            myImage[3].SetActive(false);
            myImage[2].SetActive(true);

            BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
            myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);
            //SceneManager.LoadScene("Level3");
            //FadeInOut.instance.SceneFadeInOut("Level3");
        }
        else
        {
            BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
            myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[1]);
        }
    }

    public void GoToLevel４()
    {
        if (clearedLevel >= 2)
        {
            DisplayButton.text = "Level4";
            SelectButtonOn();

            SelectedBtn.anchoredPosition = new Vector2(0f, 7f);
            SelectedBtn.localScale = new Vector2(-1f, 1f);

            myImage[0].SetActive(false);
            myImage[1].SetActive(false);
            myImage[2].SetActive(false);
            myImage[3].SetActive(true);

            BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
            myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);
            //SceneManager.LoadScene("Level3");
            //FadeInOut.instance.SceneFadeInOut("Level3");
        }
        else
        {
            BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
            myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[1]);
        }
    }

    public void SelectButtonOn()
    {
        string temp = DisplayButton.text.Substring(5);
        int levelNumber = int.Parse(temp);
        PlayerPrefs.SetInt("Level", levelNumber);

        if (!OnStartBtn.activeSelf)
        {
            OnStartBtn.SetActive(true);
        }

        if (!OnDirectionPanel.activeSelf)
        {
            OnDirectionPanel.SetActive(true);
        }

        if (levelNumber == 1)
        {
            directionsText.text = Directions[0];
        }
        else if (levelNumber == 2)
        {
            directionsText.text = Directions[1];
        }
        else if (levelNumber == 3)
        {
            directionsText.text = Directions[2];
        }
        else if (levelNumber == 4)
        {
            directionsText.text = Directions[3];
        }

    }
}
```
![image](https://user-images.githubusercontent.com/55220866/206658111-4a4b265e-aa72-4d20-99d0-fe5ad8111e32.png)
![image](https://user-images.githubusercontent.com/55220866/206658231-273b021e-2867-4a75-902e-cf5f20de46e8.png)

### 參考資料

[Array](https://docs.unity3d.com/2020.1/Documentation/ScriptReference/Array.html)
---------------------------------------------------------------
### 優化

### [How to get name of button that was clicked?](https://answers.unity.com/questions/828666/46-how-to-get-name-of-button-that-was-clicked.html)
