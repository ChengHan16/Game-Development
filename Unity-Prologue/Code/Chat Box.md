### 單對話框顯示
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class Sign : MonoBehaviour
{
    Vector3 OpenPosition;

    public GameObject dialogBox;
    public Text dialogBoxText;
    public string signText;
    private bool isPlayerOnSign,itemOn;

    GameObject myPlayer, myChatItem;

    private void Awake()
    {
        isPlayerOnSign = false;
        itemOn = true;

        myPlayer = GameObject.Find("Player");
        myChatItem = GameObject.Find("co-Star-1/Box-chat-Item");
    }

    private void Start()
    {
        myChatItem.gameObject.transform.parent = null;
    }

    void Update()
    {
        if(myPlayer.transform.position.x <= transform.position.x)
        {
            transform.localScale = new Vector3(-1.0f, 1.0f, 1.0f);
        }
        else if (myPlayer.transform.position.x >= transform.position.x)
        {
            transform.localScale = new Vector3(1.0f, 1.0f, 1.0f);
        }

        OpenPosition = new Vector3(transform.position.x + 4.0f, transform.position.y + 4.0f, transform.position.z);
        dialogBox.transform.position = OpenPosition;

        if (Input.GetKeyDown(KeyCode.Return) && isPlayerOnSign || Input.GetKeyDown(KeyCode.KeypadEnter) && isPlayerOnSign)
        {
            dialogBox.SetActive(true);
            myChatItem.SetActive(false);
        }

        foreach (KeyCode vKey in System.Enum.GetValues(typeof(KeyCode)))
        {
            if (Input.GetKey(vKey))
            {
                //your code here
                Debug.Log(vKey);
            }
        }
    }

    private void OnTriggerEnter2D(Collider2D other)
    {
        if (other.gameObject.CompareTag("Player") 
            && other.GetType().ToString() == "UnityEngine.BoxCollider2D")
        {
            dialogBoxText.text = signText;
            isPlayerOnSign = true;
        }
    }

    private void OnTriggerExit2D(Collider2D other)
    {
        if (other.gameObject.CompareTag("Player") 
            && other.GetType().ToString() == "UnityEngine.BoxCollider2D")
        {
            isPlayerOnSign = false;
            dialogBox.SetActive(false);
            myChatItem.SetActive(true);
        }
    }
}
```
### 多層對話模式
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class Sign : MonoBehaviour
{
    Vector3 OpenPosition;

    public GameObject dialogBox;
    public Text dialogBoxText;
    public string signText, signText1;
    private bool isPlayerOnSign, chatOpen;

    public int chatarray;

    GameObject myPlayer, myChatItem;

    private void Awake()
    {
        isPlayerOnSign = false;
        chatOpen = false;
        chatarray = 0;

        myPlayer = GameObject.Find("Player");
        myChatItem = GameObject.Find("co-Star-1/Box-chat-Item");
    }

    private void Start()
    {
        myChatItem.gameObject.transform.parent = null;
    }

    void Update()
    {
        if(myPlayer.transform.position.x <= transform.position.x)
        {
            transform.localScale = new Vector3(-1.0f, 1.0f, 1.0f);
        }
        else if (myPlayer.transform.position.x >= transform.position.x)
        {
            transform.localScale = new Vector3(1.0f, 1.0f, 1.0f);
        }

        OpenPosition = new Vector3(transform.position.x + 4.0f, transform.position.y + 4.0f, transform.position.z);
        dialogBox.transform.position = OpenPosition;

        if (Input.GetKeyDown(KeyCode.Return) && isPlayerOnSign || Input.GetKeyDown(KeyCode.KeypadEnter) && isPlayerOnSign)
        {
            dialogBox.SetActive(true);
            myChatItem.SetActive(false);
            chatarray += 1;
        }

        foreach (KeyCode vKey in System.Enum.GetValues(typeof(KeyCode)))
        {
            if (Input.GetKey(vKey))
            {
                //your code here
                Debug.Log(vKey);
            }
        }

        if (chatOpen)
        {
            if (chatarray == 1)
            {
                dialogBoxText.text = signText;
            }
            else if (chatarray == 2)
            {
                dialogBoxText.text = signText1;
            }
        }
    }

    private void OnTriggerEnter2D(Collider2D other)
    {
        if (other.gameObject.CompareTag("Player") 
            && other.GetType().ToString() == "UnityEngine.BoxCollider2D")
        {
            isPlayerOnSign = true;
            chatOpen = true;
        }
    }

    private void OnTriggerExit2D(Collider2D other)
    {
        if (other.gameObject.CompareTag("Player") 
            && other.GetType().ToString() == "UnityEngine.BoxCollider2D")
        {
            isPlayerOnSign = false;
            dialogBox.SetActive(false);
            myChatItem.SetActive(true);

            chatarray = 0;
        }
    }
}
```
---
## 完整版
### dialogBox
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class Sign : MonoBehaviour
{
    Vector3 OpenPosition;

    public GameObject dialogBox;
    public Text dialogBoxText;
    public string signText, signText1;
    private bool isPlayerOnSign, chatOpen;

    public int chatarray;

    GameObject myPlayer, myChatItem;
    HintText myHintText;

    private void Awake()
    {
        isPlayerOnSign = false;
        chatOpen = false;
        chatarray = 0;

        myPlayer = GameObject.Find("Player");
        myChatItem = GameObject.Find("co-Star-1/Box-chat-Item");
        myHintText = FindObjectOfType<HintText>();//.GetComponentInParent<HintText>();
    }

    private void Start()
    {
        myChatItem.gameObject.transform.parent = null;
        StartCoroutine("StartClose");
    }

    void Update()
    {
        if(myPlayer.transform.position.x <= transform.position.x)
        {
            transform.localScale = new Vector3(-1.0f, 1.0f, 1.0f);
        }
        else if (myPlayer.transform.position.x >= transform.position.x)
        {
            transform.localScale = new Vector3(1.0f, 1.0f, 1.0f);
        }

        OpenPosition = new Vector3(transform.position.x + 4.0f, transform.position.y + 4.0f, transform.position.z);
        dialogBox.transform.position = OpenPosition;

        if (Input.GetKeyDown(KeyCode.Return) && isPlayerOnSign || Input.GetKeyDown(KeyCode.KeypadEnter) && isPlayerOnSign)
        {
            dialogBox.SetActive(true);
            myChatItem.SetActive(false);
            chatarray += 1;
        }

        foreach (KeyCode vKey in System.Enum.GetValues(typeof(KeyCode)))
        {
            if (Input.GetKey(vKey))
            {
                //your code here
                Debug.Log(vKey);
            }
        }

        if (chatOpen)
        {
            if (chatarray == 1)
            {
                dialogBoxText.text = signText;
            }
            else if (chatarray == 2)
            {
                dialogBoxText.text = signText1;
            }
        }
    }

    private void OnTriggerEnter2D(Collider2D other)
    {
        if (other.gameObject.CompareTag("Player") 
            && other.GetType().ToString() == "UnityEngine.BoxCollider2D")
        {
            isPlayerOnSign = true;
            chatOpen = true;
        }
    }

    private void OnTriggerExit2D(Collider2D other)
    {
        if (other.gameObject.CompareTag("Player") 
            && other.GetType().ToString() == "UnityEngine.BoxCollider2D")
        {
            isPlayerOnSign = false;
            dialogBox.SetActive(false);
            myChatItem.SetActive(true);

            chatarray = 0;
            myHintText.textColor = 0;
            myHintText.text.color = new Color(myHintText.text.color.r, myHintText.text.color.g, myHintText.text.color.b, 0.0f);
        }
    }

    IEnumerator StartClose()
    {
        yield return new WaitForSeconds(0.002f);
        dialogBox.SetActive(false);
    }
}
```
### HintText
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class HintText : MonoBehaviour
{
    public Text text;
    public int hintRun;
    public float textColor;

    public bool CheckHint;

    private void Awake()
    {
        text = GameObject.Find("DialogBoxGroup/DialogBox/HintText").GetComponent<Text>();

        hintRun = 0;
        textColor = 0.0f;
        CheckHint = true;

    }
    void Update()
    {
        Hint();
        Debug.Log(CheckHint);
    }

    public void Hint()
    {
        StartCoroutine("HintColor");
    }

    IEnumerator HintColor()
    {
        yield return new WaitForSecondsRealtime(0.5f);

        if (textColor > 1.0f)
        {
            CheckHint = false;
        }
        else if (textColor < 0.001f)
        {
            CheckHint = true;
        }

        if (CheckHint)
        {
            textColor += 0.002f;
            textColor = Mathf.Round(textColor * 1000) / 1000;
        }
        else if (!CheckHint)
        {
            textColor -= 0.002f;
            textColor = Mathf.Round(textColor * 1000) / 1000;
        }

        text.color = new Color(text.color.r, text.color.g, text.color.b, textColor);
    }
}
```

[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.]([https://drive.google.com/drive/folders/1SenjKaqiSICDc1Ea0iObWAcNkyQJHZeL?usp=sharing](https://drive.google.com/drive/folders/1TiVbADsiW1wIgNw5TkP0kGlrldsuC-mn?usp=sharing))
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
