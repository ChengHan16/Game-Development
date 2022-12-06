
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using TMPro;
using UnityEngine.SceneManagement;

public class Scroll : MonoBehaviour
{
    public TextMeshProUGUI DisplayButton, LevelName;
    public Button StartButton;
    public int Level;

    public void QuitApplication()
    {
        Application.Quit();
    }

    public void StartBtn()
    {
        SceneManager.LoadScene("Level" + PlayerPrefs.GetInt("Level"));
    }

    public void returnMainmenu()
    {
        SceneManager.LoadScene("Sample 2.0");
    }

    public void SelectLevel1()
    {
        DisplayButton.text = "Level1";
        
        string temp = DisplayButton.text.Substring(5);
        int levelNumber = int.Parse(temp);
        PlayerPrefs.SetInt("Level", levelNumber);

        Debug.Log(levelNumber);
        LevelName.text = levelNumber.ToString();
    }
    public void SelectLevel2()
    {
        DisplayButton.text = "Level2"; 
        
        string temp = DisplayButton.text.Substring(5);
        int levelNumber = int.Parse(temp);
        PlayerPrefs.SetInt("Level", levelNumber);

        Debug.Log(levelNumber);
        LevelName.text = levelNumber.ToString();
    }
    public void SelectLevel3()
    {
        DisplayButton.text = "Level3";

        string temp = DisplayButton.text.Substring(5);
        int levelNumber = int.Parse(temp);
        PlayerPrefs.SetInt("Level", levelNumber);

        Debug.Log(levelNumber);
        LevelName.text = levelNumber.ToString();
    }
    public void SelectLevel4()
    {
        DisplayButton.text = "Level4";

        string temp = DisplayButton.text.Substring(5);
        int levelNumber = int.Parse(temp);
        PlayerPrefs.SetInt("Level", levelNumber);

        Debug.Log(levelNumber);
        LevelName.text = levelNumber.ToString();
    }
}
```
![image](https://user-images.githubusercontent.com/55220866/205992552-e989ebb4-5f72-4ea2-a464-81a910fd93a1.png)

![image](https://user-images.githubusercontent.com/55220866/205992288-24b2c571-e368-45a4-874f-ccbd229ca229.png)
