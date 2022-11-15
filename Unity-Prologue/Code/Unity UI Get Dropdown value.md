using UnityEngine.UI;
using TMPro;

```C#
public class ScreenController : MonoBehaviour
{
    public TMP_Dropdown ddFruites;

    void Start()
    {
        //myDropdown = GetComponentInParent<DropdownController>();
        Screen.fullScreen = true;

        ddFruites.onValueChanged.AddListener(delegate
        {
            ddFruitesValueChangeHappened(ddFruites);
        });
    }

    public void ddFruitesValueChangeHappened(TMP_Dropdown sender)
    {
        Debug.Log(sender.value);
    }
}
```

### 參考資料
#### Mohammad Faizan Khan [Unity3d How To - Unity UI Get Dropdown value](https://www.youtube.com/watch?v=FteXwEdED0Y)
