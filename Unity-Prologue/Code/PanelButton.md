```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;

public class PanelButtonScript : MonoBehaviour
{
    public GameObject selectPanel, levelSelectButton, mainMenuButton, replayButton;
    
    public void Quit()
    {
       Application.Quit();
    }

    public void ReplayButton()
    {
        BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
        myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);

        string sceneName = SceneManager.GetActiveScene().name;
        FadeInOut.instance.SceneFadeInOut(sceneName);
        //SceneManager.LoadScene(sceneName);
        //Time.timeScale = 1.0f;
    }

    public void MainMenuButton()
    {
        BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
        myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);

        FadeInOut.instance.SceneFadeInOut("MainMenu");
        //SceneManager.LoadScene("MainMenu");
        //Time.timeScale = 1.0f;
    }

    public void LevelSelectButton()
    {
        BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
        myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);

        FadeInOut.instance.SceneFadeInOut("LevelSelect");
        //SceneManager.LoadScene("LevelSelect");
        //Time.timeScale = 1.0f;
    }

    public void YesButton()
    {
        PlayerPrefs.DeleteAll();
        IsFirstTimePlayCheck checkScript = GameObject.Find("IsFirstTimePlayCheck").GetComponent<IsFirstTimePlayCheck>();
        checkScript.FirstTimePlayState();

        RectTransform DataDeleteImage = GameObject.Find("UICanvas/DataDeleteImage").GetComponent<RectTransform>();
        DataDeleteImage.anchoredPosition = new Vector2(0f, 1500f);

        BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
        myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);
    }

    public void NoButton()
    {
        RectTransform DataDeleteImage = GameObject.Find("UICanvas/DataDeleteImage").GetComponent<RectTransform>();
        DataDeleteImage.anchoredPosition = new Vector2(0f, 1500f);

        BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
        myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);
    }

    public void DataDeleteButton()
    {
        RectTransform DataDeleteImage = GameObject.Find("UICanvas/DataDeleteImage").GetComponent<RectTransform>();
        DataDeleteImage.anchoredPosition = new Vector2(0f, -100f);

        BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
        myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);
    }

    public void setSelectPanelOn()
    {
        selectPanel.SetActive(true);
    }

    public void setSelectPanelOff()
    {
        BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
        myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);

        selectPanel.SetActive(false);
        Time.timeScale = 1.0f;
    }

    private void Update()
    {
        Scene currentScene = SceneManager.GetActiveScene();
        string sceneName = currentScene.name;

        if (sceneName != "MainMenu")
        {
            if (Input.GetKeyDown(KeyCode.Escape))
            {
                selectPanel.SetActive(true);
                Time.timeScale = 0f;
            }
        }
    }

    public void MainMenuPlayButton()
    {
        GameObject mainMenuPlayer = GameObject.Find("MainMenuPlayer");
        Animator myAnim = mainMenuPlayer.GetComponent<Animator>();
        myAnim.SetBool("Run", true);

        GameObject playButton = GameObject.Find("UICanvas/PlayeButton");
        playButton.SetActive(false);

        BGMController myBGM = GameObject.Find("BGMController").GetComponent<BGMController>();
        myBGM.myAudioSource.PlayOneShot(myBGM.myButtonClip[0]);

        //SceneManager.LoadScene("LevelSelect");
        FadeInOut.instance.SceneFadeInOut("LevelSelect");
    }
}
```
![image](https://user-images.githubusercontent.com/55220866/197399896-9bdde28c-85e1-42d1-a2e1-65986d63cb07.png)
![image](https://user-images.githubusercontent.com/55220866/197399900-98f294ad-1bba-4610-9a05-18da826aa82f.png)
### FadeInOut
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;

public class FadeInOut : MonoBehaviour
{
    public static FadeInOut instance;
    public GameObject fadeInOutImage;
    public Animator myAnim;

    private void Awake()
    {
        if (instance != null)
        {
            Destroy(this.gameObject);
        }
        else
        {
            instance = this;
            DontDestroyOnLoad(this.gameObject);
        }
    }

    public void SceneFadeInOut(string levelName)
    {
        
        StartCoroutine(SceneFadeInOut2(levelName));
    }

    IEnumerator SceneFadeInOut2(string levelName)
    {
        fadeInOutImage.SetActive(true);

        yield return new WaitForSecondsRealtime(1.0f);
        SceneManager.LoadScene(levelName);
        myAnim.Play("FadeOut");

        yield return new WaitForSecondsRealtime(0.5f);
        fadeInOutImage.SetActive(false);
        Time.timeScale = 1.0f;
    }
}
```
![image](https://user-images.githubusercontent.com/55220866/197399996-1bfc63c6-3146-499d-9f76-54bdf8c7a6ff.png)
![image](https://user-images.githubusercontent.com/55220866/197400003-71b7844f-78b6-4274-983a-3acb1c3af7c5.png)

### q
![image](https://user-images.githubusercontent.com/55220866/197400020-7362b882-0293-4fab-a2dd-79a6356e3147.png)
![image](https://user-images.githubusercontent.com/55220866/197400028-a5947e00-9a5d-416c-b02b-1fdbcf6ab473.png)





