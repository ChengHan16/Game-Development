### Control Caption 控制說明提示
![image](https://user-images.githubusercontent.com/55220866/194050701-18b28a8d-ac20-4373-8b80-c5c4a6300df1.png)
![image](https://user-images.githubusercontent.com/55220866/194050736-273478d7-4ecc-4087-ad5b-c8dbbf0c3fc7.png)
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using TMPro;

public class CaptionMove : MonoBehaviour
{
    public TextMeshProUGUI Text;
    public GameObject MoveCaption, myPLayer, TMPText, center;
    public string[] Sentences;
    public float DialogueSpeed;

    public bool DialogueNoEnter = false;

    private int Index = 0;

    Vector3 setPosition, TextPosition;

    void Start()
    {
        StartCoroutine("resetPosition");
    }

    void Update()
    {
        setPosition = new Vector3(myPLayer.transform.position.x + 2.0f, myPLayer.transform.position.y + 2.0f, myPLayer.transform.position.z);
        MoveCaption.transform.position = setPosition;
    }

    private void FixedUpdate()
    {
        TextPosition = new Vector3(myPLayer.transform.position.x + 6.0f, myPLayer.transform.position.y + 2.0f, myPLayer.transform.position.z);
        Text.transform.position = TextPosition;

        if (Vector3.Distance(myPLayer.transform.position, center.transform.position) > 6.0f)
        {
            Index = 0;
        }
        else if (Vector3.Distance(myPLayer.transform.position, center.transform.position) > 8.5f)
        {
            Text.text = "";
            Index = 0;
        }
    }

    private void OnTriggerEnter2D(Collider2D collision)
    {
        if(collision.tag == "Player")
        {
            MoveCaption.SetActive(true);
            TMPText.SetActive(true);
            NextSentece();
        }
    }

    private void OnTriggerExit2D(Collider2D other)
    {
        if (other.gameObject.CompareTag("Player")
            && other.GetType().ToString() == "UnityEngine.BoxCollider2D")
        {
            MoveCaption.SetActive(false);
            TMPText.SetActive(false);
            Text.text = "";
            Index = 0;
        }
    }

    void NextSentece()
    {
        if (Index <= Sentences.Length - 1)
        {
            Text.text = "";
            StartCoroutine("WriteSentence");
        }
        else
        {
            Index = 0;
        }
    }

    IEnumerator WriteSentence()
    {
        foreach (char Character in Sentences[Index].ToCharArray())
        {
            Text.text += Character;
            yield return new WaitForSeconds(DialogueSpeed);
        }
        Index++;
    }

    IEnumerator resetPosition()
    {
        yield return new WaitForSeconds(0.001f);
        MoveCaption.SetActive(false);
        TMPText.SetActive(false);
    }
}
```
![image](https://user-images.githubusercontent.com/55220866/194053388-312ca9ee-4bbf-4eee-a76a-420b61374a74.png)

https://youtu.be/svHiOxPmT6I
