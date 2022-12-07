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
