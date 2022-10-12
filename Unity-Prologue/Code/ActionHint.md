#### Movehint
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using TMPro;

public class Movehint : MonoBehaviour
{
    public TextMeshProUGUI Text;
    public GameObject MoveHintImg, myPLayer, TMPText;
    public string[] Sentences;
    public float DialogueSpeed, ImgX, ImgY, textpositionX, textpositionY;

    bool IsKeyboardOn = false;
    Animator myAnim;
    
    private int Index = 0;

    Vector3 setPosition, TextPosition;

    private void Awake()
    {
        myAnim = GameObject.Find("MoveControlHint/MoveHintImg").GetComponent<Animator>();
    }

    void Start()
    {
        StartCoroutine("resetPosition");
        StartCoroutine("starhint");
        StartCoroutine("KeyboardOn");
    }

    void Update()
    {
        setPosition = new Vector3(myPLayer.transform.position.x + ImgX, myPLayer.transform.position.y + ImgY, myPLayer.transform.position.z);
        MoveHintImg.transform.position = setPosition;

        if (Input.GetKeyDown(KeyCode.A) && IsKeyboardOn || Input.GetKeyDown(KeyCode.D) && IsKeyboardOn)
        {
            StartCoroutine("Destoryhint");
        }
    }

    private void FixedUpdate()
    {
        TextPosition = new Vector3(myPLayer.transform.position.x + textpositionX, myPLayer.transform.position.y + textpositionY, myPLayer.transform.position.z);
        Text.transform.position = TextPosition; 
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
        MoveHintImg.SetActive(false);
        TMPText.SetActive(false);
    }

    IEnumerator starhint()
    {
        yield return new WaitForSeconds(2.0f);
        MoveHintImg.SetActive(true);
        TMPText.SetActive(true);
        NextSentece();
    }

    IEnumerator KeyboardOn()
    {
        yield return new WaitForSeconds(3.0f);
        IsKeyboardOn = true;
    }

    IEnumerator Destoryhint()
    {
        yield return new WaitForSeconds(2.0f);
        myAnim.SetTrigger("hintDisable");

        yield return new WaitForSeconds(0.8f);
        Destroy(this.gameObject);
    }
}
```
![image](https://user-images.githubusercontent.com/55220866/195292408-2d037999-3552-4564-a0e5-a6bd0a7a0615.png)
![image](https://user-images.githubusercontent.com/55220866/195292786-2d85599a-09fb-408c-b6ec-cba0f369226d.png)
---
#### ActionDescription
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using TMPro;

public class ActionDescription : MonoBehaviour
{
    public KeyCode EnterCode;
    public TextMeshProUGUI Text;
    public GameObject actionhint, myPLayer, TMPText;
    public string[] Sentences;
    public float DialogueSpeed, ImgX, ImgY, textpositionX, textpositionY, disableTime;
    public bool isText = true;

    BoxCollider2D myCollider;

    private int Index = 0;

    Vector3 setPosition, TextPosition;

    private void Awake()
    {
        myCollider = GetComponent<BoxCollider2D>();
    }

    void Start()
    {
        StartCoroutine("resetPosition");
    }

    void Update()
    {
        setPosition = new Vector3(myPLayer.transform.position.x + ImgX, myPLayer.transform.position.y + ImgY, myPLayer.transform.position.z);
        actionhint.transform.position = setPosition;

        if (Input.GetKeyDown(EnterCode))
        {
            StartCoroutine("DisableHint");
        }
    }

    private void FixedUpdate()
    {
        TextPosition = new Vector3(myPLayer.transform.position.x + textpositionX, myPLayer.transform.position.y + textpositionY, myPLayer.transform.position.z);
        Text.transform.position = TextPosition;
    }

    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.tag == "Player")
        {
            actionhint.SetActive(true);
            TMPText.SetActive(true);
            NextSentece();
        }
    }

    private void OnTriggerExit2D(Collider2D other)
    {
        if (other.gameObject.CompareTag("Player")
            && other.GetType().ToString() == "UnityEngine.BoxCollider2D")
        {
            //actionhint.SetActive(false);
            //TMPText.SetActive(false);
            //Index = 0;
        }
    }

    void NextSentece()
    {
        if (Index <= Sentences.Length - 1)
        {
            Text.text = "";
            if (isText)
            {
                StartCoroutine("WriteSentence");
            }
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
        isText = false;
        Destroy(myCollider.GetComponent<BoxCollider2D>());
    }

    IEnumerator resetPosition()
    {
        yield return new WaitForSeconds(0.001f);
        actionhint.SetActive(false);
        TMPText.SetActive(false);
    }

    IEnumerator DisableHint()
    {
        yield return new WaitForSeconds(disableTime);
        Destroy(this.gameObject);
    }
}
```
![image](https://user-images.githubusercontent.com/55220866/195292544-8bcb2e41-90f1-4c24-8679-b872ba7b7e3f.png)
![image](https://user-images.githubusercontent.com/55220866/195292874-0a0c94b1-dfc7-42c9-b42f-5bbdd10fb00d.png)

![image](https://user-images.githubusercontent.com/55220866/195292624-cf406db2-a527-40d2-bc2a-2b61c40c55a4.png)



https://youtu.be/TRsjAdGFbYQ
