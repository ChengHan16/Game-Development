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

        if (Input.GetKeyDown(KeyCode.Return) || Input.GetKeyDown(KeyCode.KeypadEnter) && isPlayerOnSign)
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
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://github.com/ChengHan16/Game-Development/blob/main/Unity-Prologue/Code/Chat%20Box.md)
[.](https://drive.google.com/drive/folders/1SenjKaqiSICDc1Ea0iObWAcNkyQJHZeL?usp=sharing)
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
