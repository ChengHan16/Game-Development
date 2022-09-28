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
[.](https://drive.google.com/drive/folders/1TiVbADsiW1wIgNw5TkP0kGlrldsuC-mn)
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
----
### Chat Box II (Advanced / evolution)



![image](https://user-images.githubusercontent.com/55220866/192778855-e7cd4cc9-1589-490c-a9bd-44362365df97.png)

![image](https://user-images.githubusercontent.com/55220866/192778820-b000a6b3-1062-4c4b-9e55-02017967a0c9.png)
![image](https://user-images.githubusercontent.com/55220866/192778958-a38a2ad2-c496-49f4-b20b-a381e2472d5b.png)
![image](https://user-images.githubusercontent.com/55220866/192779031-93cdda17-ec82-46a3-b20f-e8a34f9a3f73.png)
![image](https://user-images.githubusercontent.com/55220866/192779059-ebdc023b-3b66-414e-91f1-127ffcc63958.png)
![image](https://user-images.githubusercontent.com/55220866/192779135-4fdbfbaa-2370-4067-b653-d3dedb6d5ed3.png)


![image](https://user-images.githubusercontent.com/55220866/192778490-71224224-89ad-4cae-98bc-f19140ef150d.png)
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using TMPro;

public class DialogueController : MonoBehaviour
{
    public TextMeshProUGUI DialogueText;
    public GameObject coStar, myPlayer;
    public string[] Sentences;
    public float DialogueSpeed;

    private int Index = 0;
    private bool DialogueNoEnter = false;
    
    void Start()
    {
        
    }

    void Update()
    {
        if (!DialogueNoEnter)
        {
            if (Input.GetKeyDown(KeyCode.Return) || Input.GetKeyDown(KeyCode.KeypadEnter))
            {
                DialogueNoEnter = true;
                NextSentece();
            }
        }
        Debug.Log("Index" + "：" + Index);
        Debug.Log("DialogueNoEnter" + "：" + DialogueNoEnter);


        //待解決，做物件套用處理，Unity Public Setting
        if(Vector3.Distance(myPlayer.transform.position, coStar.transform.position) > 2.88f)
        {
            DialogueText.text = "";
            DialogueNoEnter = false;
        }
    }

    void NextSentece()
    {
        if (Index <= Sentences.Length - 1)
        {
            DialogueText.text = "";
            StartCoroutine("WriteSentence");
        }
        else
        {
            Index = 0;
            DialogueNoEnter = false;
        }
    }

    IEnumerator WriteSentence()
    {
        foreach(char Character in Sentences[Index].ToCharArray())
        {
            DialogueText.text += Character;
            yield return new WaitForSeconds(DialogueSpeed);
        }
        DialogueNoEnter = false;
        Index ++;
    }
}
```
https://youtu.be/2JoCKldP_d0
