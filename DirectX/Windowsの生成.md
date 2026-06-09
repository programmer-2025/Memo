## DxLibとの違い
DxLibでは、DxLib_Init() でウインドウを生成できますが、Win32APIを直接実行する場合、1つの関数では生成することができません。

## 必要なもの
* main関数 - int main() ではなく、DxLibと同じ WinMain
* ウインドウクラス　-　Windows側にウインドウとして認識するためのデータ
* ウインドウプロシージャ - Windows側が送ってくれる、ウインドウの情報を引数にした、関数。

## メッセージとは？
* Windows側が送る、ウインドウに何が起こったかを示すもの。ウインドウプロシージャが呼ばれることによって、switch文をたどって目的のメッセージとして処理されます。
* WM_CREATE ： ウインドウ作成時
* WM_DESTROY ：　ウインドウが閉じられたとき

## 分解したコード
### ウインドウクラスの生成＆登録
```cpp
	//WNDCLASSEXWの参考：https://learn.microsoft.com/ja-jp/windows/win32/api/winuser/ns-winuser-wndclassexw
	WNDCLASSEXW wndClass = {};
	wndClass.cbSize = sizeof(WNDCLASSEXW); //構造体のサイズ
	wndClass.hInstance = hInstance; //インスタンス
	wndClass.lpszClassName = WINDOW_CLASS_NAME; //クラスの名前
	wndClass.lpfnWndProc = WndProc; //ウインドウプロシージャ
	wndClass.hIcon = LoadIcon(nullptr, IDI_APPLICATION); //アイコン（参考：https://learn.microsoft.com/ja-jp/windows/win32/menurc/about-icons）
	wndClass.hIconSm = LoadIcon(nullptr, IDI_WINLOGO); //小さいアイコン
	wndClass.hCursor = LoadCursor(nullptr, IDC_ARROW); //カーソル（参考：https://learn.microsoft.com/ja-jp/windows/win32/menurc/about-cursors）
	wndClass.hbrBackground = (HBRUSH)GetStockObject(WHITE_BRUSH); //背景
	RegisterClassEx(&wndClass); //ウインドウクラスを登録する関数
```


# その他
* 勉強中なので、誤解しているところが多いかもしれません。間違えがあったら、Teamsの個人メッセージか、Issuesでお願いいたします。
