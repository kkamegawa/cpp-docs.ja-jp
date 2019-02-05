---
title: TN001:ウィンドウ クラスの登録
ms.date: 11/04/2016
f1_keywords:
- vc.registration
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
ms.openlocfilehash: 4ae94d1c9c57f6c315ae482e44576ae25194c00f
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894264"
---
# <a name="tn001-window-class-registration"></a>TN001:ウィンドウ クラスの登録

このノートには、特殊なを登録する MFC ルーチンがについて説明[WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa)es の Microsoft Windows が必要とします。 特定`WNDCLASS`MFC と Windows で使用される属性については説明します。

## <a name="the-problem"></a>問題を

属性を[CWnd](../mfc/reference/cwnd-class.md)オブジェクトなど、 `HWND` Windows での処理、2 つの場所に格納されます: ウィンドウ オブジェクトと`WNDCLASS`します。 名前、`WNDCLASS`など全般的なウィンドウ作成関数に渡される[cwnd::create](../mfc/reference/cwnd-class.md#create)と[CFrameWnd::Create](../mfc/reference/cframewnd-class.md#create)で、 *lpszClassName*パラメーター。

これは、 `WNDCLASS` 4 つの手段の 1 つを登録する必要があります。

- 指定された MFC を使用して暗黙的に`WNDCLASS`します。

- Windows のコントロール (またはその他のコントロール) をサブクラス化によって暗黙的にします。

- MFC を呼び出すことによって明示的に[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)または[AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass)します。

- Windows のルーチンを呼び出すことによって明示的に[RegisterClass](/windows/desktop/api/winuser/nf-winuser-registerclassa)します。

## <a name="wndclass-fields"></a>WNDCLASS フィールド

`WNDCLASS`ウィンドウ クラスを記述するさまざまなフィールドの構造で構成されます。 次の表では、フィールドが表示され、MFC アプリケーションで使用する方法を指定します。

|フィールド|説明|
|-----------|-----------------|
|*lpfnWndProc*|ウィンドウのプロシージャである必要があります、 `AfxWndProc`|
|*cbClsExtra*|使用しない (0 にする必要があります)|
|*cbWndExtra*|使用しない (0 にする必要があります)|
|*hInstance*|自動的に[AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|
|*hIcon*|フレーム ウィンドウ、アイコンは、以下を参照してください。|
|*hCursor*|下のウィンドウで、上にマウスがときにカーソルを参照してください。|
|*hbrBackground*|背景色、以下をご覧ください。|
|*lpszMenuName*|使用されません (NULL にする必要があります)|
|*lpszClassName*|クラス名では、以下を参照してください。|

## <a name="provided-wndclasses"></a>WNDCLASSes の提供

以前のバージョンの MFC (MFC 4.0 の場合) の前に、いくつかの定義済みウィンドウ クラスが用意されています。 これらのウィンドウ クラスは既定で備わっていません。 アプリケーションを使用する必要があります`AfxRegisterWndClass`適切なパラメーターを使用します。

アプリケーションでは、指定されたリソース ID (たとえば、AFX_IDI_STD_FRAME) を持つリソースを提供する場合、MFC はそのリソースを使用します。 それ以外の場合、既定のリソースが使用されます。 アイコンに、標準的なアプリケーションのアイコンを使用すると、カーソルでは、標準の矢印カーソルを使用します。

2 つのアイコンは、1 つのドキュメント型を持つ MDI アプリケーションをサポートします。 メイン アプリケーションの 1 つのアイコン、あります windows のその他のアイコン。 アイコンが異なる複数のドキュメントの種類を追加する必要があります登録`WNDCLASS`es または使用して、 [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)関数。

`CFrameWnd::LoadFrame` 登録は、`WNDCLASS`最初のパラメーターと、次の標準属性として指定したアイコン ID を使用します。

- クラス スタイル:CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW;

- AFX_IDI_STD_FRAME アイコン

- 矢印カーソル

- COLOR_WINDOW 背景色

背景色とのカーソルの値は、 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)以降のクライアント領域は使用されません、`CMDIFrameWnd`に完全に覆わ、 **MDICLIENT**ウィンドウ。 Microsoft がサブクラス化が促進されません、 **MDICLIENT**ウィンドウは、そのため、標準の色と可能な場合、カーソルの種類に使用します。

## <a name="subclassing-and-superclassing-controls"></a>サブクラスとスーパークラス化コントロール

サブクラスまたは、Windows のスーパークラスで制御できる場合 (たとえば、 [CButton](../mfc/reference/cbutton-class.md)) クラスが自動的に取得し、`WNDCLASS`そのコントロールの Windows 実装で指定された属性。

## <a name="the-afxregisterwndclass-function"></a>AfxRegisterWndClass 関数

MFC には、ウィンドウ クラスを登録するためのヘルパー関数が用意されています。 一連の属性 (ウィンドウ クラス スタイル、カーソル、背景のブラシ、およびアイコン) を指定するには、合成名が生成され、結果のウィンドウ クラスが登録されています。 例えば以下のようにします。

```
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```

この関数は、生成された登録済みのウィンドウ クラス名の一時的な文字列を返します。 この関数の詳細については、次を参照してください。 [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)します。

返される文字列は、静的な文字列バッファーへの一時的なポインターです。 次の呼び出しまで有効です`AfxRegisterWndClass`します。 周りには、この文字列を保持する場合は、保存、 [CString](../atl-mfc-shared/using-cstring.md)この例のように、変数。

```
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...
CWnd* pWnd = new CWnd;
pWnd->Create(strWndClass, ...);

...
```

`AfxRegisterWndClass` スローされます、 [CResourceException](../mfc/reference/cresourceexception-class.md)ウィンドウ クラスが (ため不適切なパラメーター、または Windows のメモリ不足) の登録に失敗したかどうか。

## <a name="the-registerclass-and-afxregisterclass-functions"></a>RegisterClass と AfxRegisterClass 関数

実行する場合は、何もより高度なよりも`AfxRegisterWndClass`を提供する Windows API を呼び出すことができます`RegisterClass`または MFC 関数`AfxRegisterClass`します。 `CWnd`、 [CFrameWnd](../mfc/reference/cframewnd-class.md)と[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create`関数、 *lpszClassName*最初のパラメーターとして、ウィンドウ クラスの文字列名。 登録時に使用する方法に関係なく、すべての登録済みのウィンドウ クラス名を使用することができます。

使用することが重要`AfxRegisterClass`(または`AfxRegisterWndClass`) Win32 の DLL にします。 Win32 は自動的に登録解除されないため、DLL が終了したときを明示的に登録を解除する必要があります、DLL が登録されているクラス。 使用して`AfxRegisterClass`の代わりに`RegisterClass`を自動的にこの処理されます。 `AfxRegisterClass` 一意のクラスの一覧は、DLL に登録されているし、は自動的に登録を解除して、DLL の終了時に維持します。 使用すると`RegisterClass`DLL で DLL が終了したときにすべてのクラスが登録されているいないを確認する必要があります (で、 [DllMain](/windows/desktop/Dlls/dllmain)関数)。 そのために問題が発生する可能性があります`RegisterClass`別のクライアント アプリケーションが DLL を使用しようとしたときに予期せず失敗します。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)

