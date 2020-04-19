---
title: CMFCEditBrowseCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFileBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFolderBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::GetMode
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnAfterUpdate
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnBrowse
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnChangeLayout
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnDrawBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnIllegalFileName
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::SetBrowseButtonImage
helpviewer_keywords:
- CMFCEditBrowseCtrl [MFC], EnableBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFileBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFolderBrowseButton
- CMFCEditBrowseCtrl [MFC], GetMode
- CMFCEditBrowseCtrl [MFC], OnAfterUpdate
- CMFCEditBrowseCtrl [MFC], OnBrowse
- CMFCEditBrowseCtrl [MFC], OnChangeLayout
- CMFCEditBrowseCtrl [MFC], OnDrawBrowseButton
- CMFCEditBrowseCtrl [MFC], OnIllegalFileName
- CMFCEditBrowseCtrl [MFC], SetBrowseButtonImage
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
ms.openlocfilehash: db99c5e72e84bb359184f4c62594fcddff7d8ff6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505350"
---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl クラス

クラス`CMFCEditBrowseCtrl`は、必要に応じて [参照] ボタンを含む編集可能なテキストボックスである、edit browse コントロールをサポートします。 ユーザーが参照ボタンをクリックすると、このコントロールはカスタム動作を実行するか、ファイル参照またはフォルダー参照を含む標準ダイアログ ボックスを表示します。

## <a name="syntax"></a>構文

```
class CMFCEditBrowseCtrl : public CEdit
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|既定のコンストラクターです。|
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCEditBrowseCtrl:: EnableBrowseButton](#enablebrowsebutton)|[参照] ボタンを有効または無効にします (非表示にします)。|
|[CMFCEditBrowseCtrl:: EnableFileBrowseButton](#enablefilebrowsebutton)|[参照] ボタンを有効にし、[参照の編集] コントロールを*ファイル参照*モードにします。|
|[CMFCEditBrowseCtrl:: EnableFolderBrowseButton](#enablefolderbrowsebutton)|[参照] ボタンを有効にし、[参照の編集] コントロールを*フォルダー参照*モードにします。|
|[CMFCEditBrowseCtrl:: GetMode](#getmode)|現在のブラウズモードを返します。|
|[CMFCEditBrowseCtrl:: OnAfterUpdate](#onafterupdate)|参照操作の結果によってエディット参照コントロールが更新された後に、フレームワークによって呼び出されます。|
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|ユーザーが参照ボタンをクリックした後に、フレームワークによって呼び出されます。|
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|現在の編集参照コントロールを再描画します。|
|[CMFCEditBrowseCtrl:: OnDrawBrowseButton](#ondrawbrowsebutton)|参照ボタンを描画するためにフレームワークによって呼び出されます。|
|[CMFCEditBrowseCtrl:: OnIllegalFileName](#onillegalfilename)|無効なファイル名が編集コントロールに入力されたときにフレームワークによって呼び出されます。|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)および[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)の Windows 関数にディスパッチされる前に、ウィンドウメッセージを変換します。 構文と詳細については、「 [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)」を参照してください。|
|[CMFCEditBrowseCtrl:: SetBrowseButtonImage](#setbrowsebuttonimage)|[参照] ボタンのカスタムイメージを設定します。|

## <a name="remarks"></a>Remarks

ファイル名またはフォルダー名を選択するには、[参照の編集] コントロールを使用します。 必要に応じて、コントロールを使用して、ダイアログボックスを表示するなどのカスタムアクションを実行します。 [参照] ボタンを表示または非表示にしたり、ボタンにカスタムラベルまたはイメージを適用したりすることができます。

[参照の編集] コントロールの*ブラウズモード*によって、[参照] ボタンを表示するかどうか、およびボタンをクリックしたときに実行されるアクションが決まります。 詳細については、「 [Getmode](#getmode)メソッド」を参照してください。

クラス`CMFCEditBrowseCtrl`は、次のモードをサポートしています。

- **カスタムモード**

   カスタムアクションは、ユーザーが [参照] ボタンをクリックしたときに実行されます。 たとえば、アプリケーション固有のダイアログボックスを表示できます。

- **ファイルモード**

   ユーザーが [参照] ボタンをクリックすると、標準の [ファイルの選択] ダイアログボックスが表示されます。

- **フォルダーモード**

   ユーザーが [参照] ボタンをクリックすると、標準の [フォルダーの選択] ダイアログボックスが表示されます。

## <a name="how-to-specify-an-edit-browse-control"></a>方法: エディット参照コントロールを指定する

次の手順を実行して、アプリケーションに edit browse コントロールを組み込みます。

1. カスタムブラウズモードを実装する場合は、 `CMFCEditBrowseCtrl`クラスから独自のクラスを派生させ、 [CMFCEditBrowseCtrl:: onbrowse](#onbrowse)メソッドをオーバーライドします。 オーバーライドされたメソッドで、カスタムの参照操作を実行し、結果を使用して、edit browse コントロールを更新します。

1. `CMFCEditBrowseCtrl`オブジェクトまたは派生したエディット参照コントロールオブジェクトを親ウィンドウオブジェクトに埋め込みます。

1. **クラスウィザード**を使用してダイアログボックスを作成する場合は、ダイアログボックスフォーム`CEdit`に編集コントロール () を追加します。 また、ヘッダーファイル内のコントロールにアクセスする変数を追加します。 ヘッダーファイルで、変数の型をから`CEdit`に`CMFCEditBrowseCtrl`変更します。 [参照の編集] コントロールが自動的に作成されます。 **クラスウィザード**を使用しない場合は、ヘッダーファイル`CMFCEditBrowseCtrl`に変数を追加し、その`Create`メソッドを呼び出します。

1. [参照の編集] コントロールをダイアログボックスに追加する場合は、 **ClassWizard**ツールを使用してデータ交換を設定します。

1. [EnableFolderBrowseButton](#enablefolderbrowsebutton)、 [EnableFileBrowseButton](#enablefilebrowsebutton)、または[EnableBrowseButton](#enablebrowsebutton)メソッドを呼び出してブラウズモードを設定し、[参照] ボタンを表示します。 [Getmode](#getmode)メソッドを呼び出して、現在のブラウズモードを取得します。

1. [参照] ボタンのカスタムイメージを提供するには、 [SetBrowseButtonImage](#setbrowsebuttonimage)メソッドを呼び出すか、 [OnDrawBrowseButton](#ondrawbrowsebutton)メソッドをオーバーライドします。

1. [参照の編集] コントロールから [参照] ボタンを削除するには、 *Benable*パラメーターを FALSE に設定して[EnableBrowseButton](#enablebrowsebutton)メソッドを呼び出します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>例

クラスの2つのメソッド ( `EnableFileBrowseButton`と)を使用する方法を次の例に示します。`EnableFolderBrowseButton` `CMFCEditBrowseCtrl` この例は、「[新しいコントロールのサンプル](../../overview/visual-cpp-samples.md)」の一部です。

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>必要条件

**ヘッダー:** afxeditbrowsectrl

##  <a name="enablebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableBrowseButton

現在の編集参照コントロールの [参照] ボタンを表示または非表示にします。

```
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
[参照] ボタンを表示する場合は TRUE。[参照] ボタンを表示しない場合は FALSE。 既定値は TRUE です。

*szLabel*<br/>
参照ボタンに表示されるラベル。 既定値は " **...** " です。

### <a name="remarks"></a>Remarks

*Benable*パラメーターが TRUE の場合は、[参照] ボタンをクリックしたときに実行するカスタムアクションを実装します。 カスタムアクションを実装するには、クラスから`CMFCEditBrowseCtrl`クラスを派生させ、その[onbrowse](#onbrowse)メソッドをオーバーライドします。

*Benable*パラメーターが TRUE の場合、コントロールのブラウズモードは`BrowseMode_Default`です。それ以外の場合、ブラウズモード`BrowseMode_None`はです。 ブラウズモードの詳細については、「 [Getmode](#getmode)メソッド」を参照してください。

##  <a name="enablefilebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFileBrowseButton

現在のエディット参照コントロールに [参照] ボタンを表示し、コントロールを*ファイル参照*モードにします。

```
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,
    LPCTSTR lpszFilter=NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```

### <a name="parameters"></a>パラメーター

*lpszDefExt*<br/>
[ファイルの選択] ダイアログ ボックスで使用する既定のファイル名拡張子を指定します。 既定値は NULL です。

*lpszFilter*<br/>
[ファイルの選択] ダイアログ ボックスで使用する既定のフィルター文字列を指定します。 既定値は NULL です。

*dwFlags*<br/>
ダイアログ ボックスのフラグ。 既定値は OFN_HIDEREADONLY と OFN_OVERWRITEPROMPT のビットごとの組み合わせ (OR) です。

### <a name="remarks"></a>Remarks

参照機能付きコントロールがファイル参照モードのときにユーザーが [参照] ボタンをクリックすると、コントロールに標準的なファイル選択のダイアログ ボックスが表示されます。

使用可能なフラグの完全な一覧については、「 [Openfilename 構造体](/windows/win32/api/commdlg/ns-commdlg-openfilenamew)」を参照してください。

##  <a name="enablefolderbrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFolderBrowseButton

現在のエディット参照コントロールに [参照] ボタンを表示し、コントロールを*フォルダー参照*モードにします。

```
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>Remarks

[参照の編集] コントロールがフォルダー参照モードであり、ユーザーが [参照] ボタンをクリックすると、コントロールに標準の [フォルダーの選択] ダイアログボックスが表示されます。

##  <a name="getmode"></a>  CMFCEditBrowseCtrl::GetMode

現在の編集参照コントロールのブラウズモードを取得します。

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>戻り値

エディット参照コントロールの現在のモードを指定する列挙値の1つ。 参照モードは、フレームワークが [参照] ボタンを表示するかどうか、およびユーザーがそのボタンをクリックしたときにどのようなアクションが実行されるかを決定します。

次の表は、可能性のある戻り値の一覧です。

|[値]|説明|
|-----------|-----------------|
|`BrowseMode_Default`|**カスタムモード**。 プログラマが定義したアクションが実行されます。|
|`BrowseMode_File`|**ファイルモード**。 標準の [ファイルブラウザー] ダイアログボックスが表示されます。|
|`BrowseMode_Folder`|**フォルダーモード**。 標準の [フォルダーブラウザー] ダイアログボックスが表示されます。|
|`BrowseMode_None`|[参照] ボタンは表示されません。|

### <a name="remarks"></a>Remarks

既定では、 `CMFCEditBrowseCtrl`オブジェクトはモードに`BrowseMode_None`初期化されます。 [CMFCEditBrowseCtrl:: EnableBrowseButton](#enablebrowsebutton)、 [CMFCEditBrowseCtrl:: EnableFileBrowseButton](#enablefilebrowsebutton)、 [CMFCEditBrowseCtrl:: EnableFolderBrowseButton](#enablefolderbrowsebutton)の各メソッドを使用して、ブラウズモードを変更します。

##  <a name="onafterupdate"></a>CMFCEditBrowseCtrl:: OnAfterUpdate

参照操作の結果によってエディット参照コントロールが更新された後に、フレームワークによって呼び出されます。

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>Remarks

カスタムアクションを実装するには、派生クラスでこのメソッドをオーバーライドします。

##  <a name="onbrowse"></a>  CMFCEditBrowseCtrl::OnBrowse

ユーザーが編集参照コントロールの [参照] ボタンをクリックした後に、フレームワークによって呼び出されます。

```
virtual void OnBrowse();
```

### <a name="remarks"></a>Remarks

このメソッドは、ユーザーが [参照の編集] コントロールの [参照] ボタンをクリックしたときにカスタムコードを実行するために使用します。 `CMFCEditBrowseCtrl`クラスから独自のクラスを派生させ、 `OnBrowse`そのメソッドをオーバーライドします。 このメソッドでは、カスタムの参照操作を実装し、必要に応じて、[参照の編集] コントロールのテキストボックスを更新します。 アプリケーションで、 [EnableBrowseButton](#enablebrowsebutton)メソッドを使用して、エディット参照コントロールを*カスタムブラウズ*モードにします。

##  <a name="onchangelayout"></a>  CMFCEditBrowseCtrl::OnChangeLayout

現在の編集参照コントロールを再描画します。

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>Remarks

このメソッドは、エディット参照コントロールのブラウズモードが変更されたときに、フレームワークによって呼び出されます。 詳細については、「 [CMFCEditBrowseCtrl:: GetMode](#getmode)」を参照してください。

##  <a name="ondrawbrowsebutton"></a>CMFCEditBrowseCtrl:: OnDrawBrowseButton

参照の編集コントロールに参照ボタンを描画するために、フレームワークによって呼び出されます。

```
virtual void OnDrawBrowseButton(
    CDC* pDC,
    CRect rect,
    BOOL bIsButtonPressed,
    BOOL bIsButtonHot);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
デバイスコンテキストへのポインター。

*矩形*<br/>
参照ボタンの外接する四角形。

*bIsButtonPressed*<br/>
ボタンが押された場合は TRUE。それ以外の場合は FALSE。

*bIsButtonHot*<br/>
ボタンが強調表示されている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

派生クラスでこの関数をオーバーライドして、[参照] ボタンの外観をカスタマイズします。

##  <a name="setbrowsebuttonimage"></a>  CMFCEditBrowseCtrl::SetBrowseButtonImage

[参照の編集] コントロールの [参照] ボタンにカスタムイメージを設定します。

```
void SetBrowseButtonImage(
    HICON hIcon,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(UINT uiBmpResId);
```

### <a name="parameters"></a>パラメーター

*hIcon*<br/>
アイコンのハンドル。

*hBitmap*<br/>
ビットマップのハンドル。

*uiBmpResId*<br/>
ビットマップのリソース ID。

*bAutoDestroy*<br/>
このメソッドが終了したときに、指定されたアイコンまたはビットマップを削除する場合は TRUE。それ以外の場合は FALSE。 既定値は TRUE です。

### <a name="remarks"></a>Remarks

このメソッドを使用して、[参照] ボタンにカスタムイメージを適用します。 既定では、[参照の編集] コントロールが*ファイル参照*モードまたは*フォルダー参照*モードになっている場合、フレームワークは標準のイメージを取得します。

##  <a name="onillegalfilename"></a>  CMFCEditBrowseCtrl::OnIllegalFileName

無効なファイル名が編集コントロールに入力されたときにフレームワークによって呼び出されます。

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>パラメーター

*strFileName*<br/>
無効なファイル名を指定します。

### <a name="return-value"></a>戻り値

このファイル名をファイルダイアログに渡すことができない場合、は FALSE を返します。 この場合、フォーカスはエディットコントロールに戻され、ユーザーは編集を続行する必要があります。 既定の実装では、無効なファイル名についてユーザーに通知するメッセージボックスが表示され、FALSE が返されます。 このメソッドをオーバーライドし、ファイル名を修正し、さらに処理するには TRUE を返すことができます。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)
