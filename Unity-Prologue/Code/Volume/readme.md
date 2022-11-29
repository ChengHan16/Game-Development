### 即時調整音量 Code
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using TMPro;

public class VolumeController : MonoBehaviour
{
    [SerializeField] private Slider volumeSlider = null;
    [SerializeField] private TextMeshProUGUI volumeTextUI;
    [SerializeField] private AudioSource BGM;

    private void Start()
    {
        BGM.volume = 1;
        volumeTextUI.text = (BGM.volume * 100).ToString();
        volumeSlider.value = BGM.volume;
    }

    public void VolumeSlider(float volume) //音量調整數值顯示
    {
        volumeTextUI.text = (volume*100).ToString("0");
    }

    public void ChangeVolume()
    {
        //AudioListener.volume = volumeSlider.value; //[Method_1]
        BGM.volume = volumeSlider.value; //[Method_2]
    }
}
```
--------------------------------------------------------------------
### 待處理更新
將音量儲存 PlayerPrefs Method
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using TMPro;

public class VolumeController : MonoBehaviour
{
    [SerializeField] private Slider volumeSlider = null;
    [SerializeField] private TextMeshProUGUI volumeTextUI;
    [SerializeField] private AudioSource BGM;

    private void Start()
    {
        BGM.volume = 1;
        volumeTextUI.text = (BGM.volume * 100).ToString();
        volumeSlider.value = BGM.volume;
    }

    public void VolumeSlider(float volume) //音量調整數值顯示
    {
        volumeTextUI.text = (volume*100).ToString("0");
    }

    public void ChangeVolume()
    {
        //AudioListener.volume = volumeSlider.value; //[Method_1]
        BGM.volume = volumeSlider.value; //[Method_2]

        //float volumeValue = volumeSlider.value;
        //PlayerPrefs.SetFloat("VolumeValue", volumeValue);
        //PlayerPrefs.GetFloat("VolumeValue", volumeValue);
        //volumeSlider.value = volumeValue;
    }
}
```
--------------------------------------------------------------------
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

    private void Awake()
    {
        myAudioSource = GetComponent<AudioSource>();
    }

    private void Update()
    {
        if (Input.GetKeyDown(KeyCode.J))
        {
            myAudioSource.PlayOneShot(myAudioClip[0]);
        }
    }

    private void Start()
    {
        myAudioSource.clip = myBGMClip[0];
        myAudioSource.Play();
        myAudioSource.volume = 1;
        volumeTextUI.text = (myAudioSource.volume * 100).ToString();
        volumeSlider.value = myAudioSource.volume;
    }

    public void VolumeSlider(float volume) //音量調整數值顯示
    {
        volumeTextUI.text = (volume*100).ToString("0");
    }
}
```
--------------------------------------------------------------------
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

    private void Awake()
    {
        myAudioSource = GetComponent<AudioSource>();


    }

    private void Start()
    {
        myAudioSource.clip = myBGMClip[0];
        myAudioSource.Play();
        //myAudioSource.volume = 1;
        volumeTextUI.text = (myAudioSource.volume * 100).ToString();
        volumeSlider.value = myAudioSource.volume;


        if (PlayerPrefs.HasKey("musicVolume"))
        {
            LoadVolume();
        }
        else
        {
            PlayerPrefs.SetFloat("musicVolume", 1);
            LoadVolume();
        }

        /*if (!PlayerPrefs.HasKey("musicVolume"))
        {
            PlayerPrefs.SetFloat("musicVolume", 1);
            LoadVolume();
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

        Debug.Log(PlayerPrefs.GetFloat("musicVolume"));

        if (PlayerPrefs.HasKey("musicVolume"))
        {
            Debug.Log("The key " + "musicVolume" + " exists");
        }
        else
            Debug.Log("The key " + "musicVolume" + " does not exist");
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
        volumeSlider.value = PlayerPrefs.GetFloat("musicVolume");
    }

    public void Save()
    {
        PlayerPrefs.SetFloat("musicVolume", volumeSlider.value);
    }

    public void DeleteKey()
    {
        PlayerPrefs.DeleteAll();
    }
}
```
