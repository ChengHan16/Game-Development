
### 檢查按下哪個按鍵
```C#
foreach (KeyCode vKey in System.Enum.GetValues(typeof(KeyCode)))
{
   if (Input.GetKey(vKey))
   {
      Debug.Log(vKey);
   }
}
```
### 使用按鈕開啟菜單和關閉
`selectPanel.SetActive(!selectPanel.activeSelf);`
```C#
if (Input.GetKeyDown(KeyCode.Escape) && !settingPanel.activeSelf)
{
   selectPanel.SetActive(!selectPanel.activeSelf);
   
   if (selectPanel.activeSelf)
   {
       Time.timeScale = 0f;
   }
   else if(!selectPanel.activeSelf)
   {
       Time.timeScale = 1f;
   }
}
```
參考資料：Chris' Tutorials [Open and Close Menus with Buttons or Escape Key | Unity 2018 Game Development](https://www.youtube.com/watch?v=aN11LnlF89I)
