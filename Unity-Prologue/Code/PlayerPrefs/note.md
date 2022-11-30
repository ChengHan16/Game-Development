```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using TMPro;

public class VolumeController : MonoBehaviour
{
    public AudioClip[] myBGMClip; 
    public AudioClip[] myAudioClip;

    [SerializeField] private Slider volumeSlider = null;
    [SerializeField] private TextMeshProUGUI volumeTextUI;
    [SerializeField] private AudioSource BGM;

    [HideInInspector]
    AudioSource myAudioSource;

    ScreenController myScreenScript;

    private void Awake()
    {
        myAudioSource = GetComponent<AudioSource>();
        myScreenScript = GetComponentInParent<ScreenController>();
    }

    private void Start()
    {
        myAudioSource.clip = myBGMClip[0];
        myAudioSource.Play();
        //myAudioSource.volume = 1;
        volumeTextUI.text = (myAudioSource.volume * 100).ToString();
        volumeSlider.value = myAudioSource.volume;

        if (!PlayerPrefs.HasKey("musicVolume"))
        {
            PlayerPrefs.SetFloat("musicVolume", 1);
            //PlayerPrefs.SetString("Screen", FullScreenMode.ExclusiveFullScreen.ToString());
            //LoadVolume();
        }
        else
        {
            LoadVolume();
        }

        /*if (!PlayerPrefs.HasKey("Resolutionwidth"))
        {
            PlayerPrefs.SetInt("Resolutionwidth", Screen.currentResolution.width);
        }
        else
        {
            LoadVolume();
        }
        if (!PlayerPrefs.HasKey("Resolutionheight"))
        {
            PlayerPrefs.SetInt("Resolutionheight", Screen.currentResolution.height);
        }
        else
        {
            LoadVolume();
        }*/
    }

    private void Update()
    {
        if (Input.GetKeyDown(KeyCode.J))
        {
            myAudioSource.PlayOneShot(myAudioClip[0]);
        }

        /*Debug.Log(PlayerPrefs.GetFloat("musicVolume"));
        Debug.Log(PlayerPrefs.GetInt("Resolutionwidth", Screen.width));
        Debug.Log(PlayerPrefs.GetInt("Resolutionheight", Screen.height));*/
    }

    public void VolumeSlider(float volume) //音量調整數值顯示
    {
        volumeTextUI.text = (volume*100).ToString("0");
    }

    public void ChangeVolume()
    {
        AudioListener.volume = volumeSlider.value;
    }

    public void LoadVolume()
    {
        string screenMode = Screen.fullScreenMode.ToString();

        volumeSlider.value = PlayerPrefs.GetFloat("musicVolume");
        screenMode = PlayerPrefs.GetString("Screen");

        //Screen.SetResolution(PlayerPrefs.GetInt("Resolutionwidth"), PlayerPrefs.GetInt("Resolutionheight"), Screen.fullScreenMode);
    }

    public void Save()
    {
        PlayerPrefs.SetFloat("musicVolume", volumeSlider.value);

        PlayerPrefs.SetString("Screen", Screen.fullScreenMode.ToString());

        /*PlayerPrefs.SetInt("Resolutionwidth", Screen.width);
        PlayerPrefs.SetInt("Resolutionheight", Screen.height);*/
    }

    public void DeleteKey()
    {
        PlayerPrefs.DeleteAll();
    }
}
```
