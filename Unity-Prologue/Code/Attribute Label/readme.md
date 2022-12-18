[Space(10)]
在 Inspector 中，和前一個變數保持一段空白的距離，參數為空白的高度

[Header("Health Settings")]
在 Inspector 中，在欄位前加入一個文字標題，參數為文字標題字串

[Range(0f, 1f)]
讓 float 或 int 變數有一個範圍上的限制，參數為限制數值的下限與上限。在 Inspector 中，該欄位會變成一個可控制的滑桿(Slider)

[Tooltip("Health value between 0 and 100.")]
讓滑鼠游標移動到該變數欄位上時，顯示提示文字。參數為文字提示字串

[HideInInspector]
讓該變數在 Inspector 中隱藏，即使被宣告為 Public 也看不到它

[SerializeField]
讓該變數在 Inspector 中顯示，即使被宣告為 Private 也看得到它

[Multiline(5)]
讓該字串變數在 Inspector 中顯示為可輸入多行的文字區塊，參數為文字區塊的最大行數

[TextArea(0, 10)]
讓該字串變數在 Inspector 中顯示為可輸入多行、帶有滑桿的文字區塊，參數為文字區塊的最小和最大行數

參考資料：
[Unity Editor 自製編輯器(二) - Attribute](https://dotblogs.com.tw/coolgamedevnote/2018/03/04/230939)
[Unity常用[xxx]用法特性](https://blog.csdn.net/FifthGently/article/details/78363364)