
### 參考資料：

*相機人我的超人 my Cinemachine Hero*

[How to change values from a script [ScreenX for example]?](https://forum.unity.com/threads/how-to-change-values-from-a-script-screenx-for-example.630844/)

> Notice I am using `CinemachineFramingTransposer` no `CinemachineComposer`
```C#
cinemachineframingTransposer = GetComponent<CinemachineVirtualCamera>().GetCinemachineComponent<CinemachineFramingTransposer>();
```
--------------------------------------------------------------------------------------------------------------------------------
[【Cinemachine 智能相機教程】VirtualCamera(二)：Body屬性](https://zhuanlan.zhihu.com/p/107212189)
