[Unity OnTriggerEnter2D 觸發條件](https://blog.csdn.net/weixin_43149049/article/details/101232989)

[unity脚本中防止多次触发OnTriggerEnter](https://blog.51cto.com/u_15127651/4375772)
```C#
void OnTriggerEnter2D(Collider2D col)
    {
        if (col.tag == "cherry")
        {
            col.gameObject.GetComponent<BoxCollider2D>().enabled = false;
            Destroy(col.gameObject);
            collections = collections + 1;
            cherText.text = collections.ToString();
            Debug.Log("Triggered by Cherry");
                
        }
    }
-----------------------------------
unity脚本中防止多次触发OnTriggerEnter
https://blog.51cto.com/u_15127651/4375772
```
