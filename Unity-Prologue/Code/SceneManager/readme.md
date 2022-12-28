### [SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)
```C#
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space))
        {
            StartCoroutine(LoadYourAsyncScene());
        }
    }
    
    IEnumerator LoadYourAsyncScene()
    {
        AsyncOperation asyncLoad = SceneManager.LoadSceneAsync("Scene2");

        while (!asyncLoad.isDone)
        {
            yield return null;
        }
    }
```
### [Unity異步加載場景SceneManager.LoadSceneAsync與AsyncOperation的使用](https://blog.csdn.net/qq_42462109/article/details/83096135)
