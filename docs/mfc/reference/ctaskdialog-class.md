---
title: CTaskDialog Class
ms.date: 11/19/2018
f1_keywords:
- CTaskDialog
- AFXTASKDIALOG/CTaskDialog
- AFXTASKDIALOG/CTaskDialog::CTaskDialog
- AFXTASKDIALOG/CTaskDialog::AddCommandControl
- AFXTASKDIALOG/CTaskDialog::AddRadioButton
- AFXTASKDIALOG/CTaskDialog::ClickCommandControl
- AFXTASKDIALOG/CTaskDialog::ClickRadioButton
- AFXTASKDIALOG/CTaskDialog::DoModal
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonCount
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonFlag
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonId
- AFXTASKDIALOG/CTaskDialog::GetOptions
- AFXTASKDIALOG/CTaskDialog::GetSelectedCommandControlID
- AFXTASKDIALOG/CTaskDialog::GetSelectedRadioButtonID
- AFXTASKDIALOG/CTaskDialog::GetVerificationCheckboxState
- AFXTASKDIALOG/CTaskDialog::IsCommandControlEnabled
- AFXTASKDIALOG/CTaskDialog::IsRadioButtonEnabled
- AFXTASKDIALOG/CTaskDialog::IsSupported
- AFXTASKDIALOG/CTaskDialog::LoadCommandControls
- AFXTASKDIALOG/CTaskDialog::LoadRadioButtons
- AFXTASKDIALOG/CTaskDialog::NavigateTo
- AFXTASKDIALOG/CTaskDialog::OnCommandControlClick
- AFXTASKDIALOG/CTaskDialog::OnCreate
- AFXTASKDIALOG/CTaskDialog::OnDestroy
- AFXTASKDIALOG/CTaskDialog::OnExpandButtonClick
- AFXTASKDIALOG/CTaskDialog::OnHelp
- AFXTASKDIALOG/CTaskDialog::OnHyperlinkClick
- AFXTASKDIALOG/CTaskDialog::OnInit
- AFXTASKDIALOG/CTaskDialog::OnNavigatePage
- AFXTASKDIALOG/CTaskDialog::OnRadioButtonClick
- AFXTASKDIALOG/CTaskDialog::OnTimer
- AFXTASKDIALOG/CTaskDialog::OnVerificationCheckboxClick
- AFXTASKDIALOG/CTaskDialog::RemoveAllCommandControls
- AFXTASKDIALOG/CTaskDialog::RemoveAllRadioButtons
- AFXTASKDIALOG/CTaskDialog::SetCommandControlOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtons
- AFXTASKDIALOG/CTaskDialog::SetContent
- AFXTASKDIALOG/CTaskDialog::SetDefaultCommandControl
- AFXTASKDIALOG/CTaskDialog::SetDefaultRadioButton
- AFXTASKDIALOG/CTaskDialog::SetDialogWidth
- AFXTASKDIALOG/CTaskDialog::SetExpansionArea
- AFXTASKDIALOG/CTaskDialog::SetFooterIcon
- AFXTASKDIALOG/CTaskDialog::SetFooterText
- AFXTASKDIALOG/CTaskDialog::SetMainIcon
- AFXTASKDIALOG/CTaskDialog::SetMainInstruction
- AFXTASKDIALOG/CTaskDialog::SetOptions
- AFXTASKDIALOG/CTaskDialog::SetProgressBarMarquee
- AFXTASKDIALOG/CTaskDialog::SetProgressBarPosition
- AFXTASKDIALOG/CTaskDialog::SetProgressBarRange
- AFXTASKDIALOG/CTaskDialog::SetProgressBarState
- AFXTASKDIALOG/CTaskDialog::SetRadioButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckbox
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckboxText
- AFXTASKDIALOG/CTaskDialog::SetWindowTitle
- AFXTASKDIALOG/CTaskDialog::ShowDialog
- AFXTASKDIALOG/CTaskDialog::TaskDialogCallback
helpviewer_keywords:
- CTaskDialog [MFC], CTaskDialog
- CTaskDialog [MFC], AddCommandControl
- CTaskDialog [MFC], AddRadioButton
- CTaskDialog [MFC], ClickCommandControl
- CTaskDialog [MFC], ClickRadioButton
- CTaskDialog [MFC], DoModal
- CTaskDialog [MFC], GetCommonButtonCount
- CTaskDialog [MFC], GetCommonButtonFlag
- CTaskDialog [MFC], GetCommonButtonId
- CTaskDialog [MFC], GetOptions
- CTaskDialog [MFC], GetSelectedCommandControlID
- CTaskDialog [MFC], GetSelectedRadioButtonID
- CTaskDialog [MFC], GetVerificationCheckboxState
- CTaskDialog [MFC], IsCommandControlEnabled
- CTaskDialog [MFC], IsRadioButtonEnabled
- CTaskDialog [MFC], IsSupported
- CTaskDialog [MFC], LoadCommandControls
- CTaskDialog [MFC], LoadRadioButtons
- CTaskDialog [MFC], NavigateTo
- CTaskDialog [MFC], OnCommandControlClick
- CTaskDialog [MFC], OnCreate
- CTaskDialog [MFC], OnDestroy
- CTaskDialog [MFC], OnExpandButtonClick
- CTaskDialog [MFC], OnHelp
- CTaskDialog [MFC], OnHyperlinkClick
- CTaskDialog [MFC], OnInit
- CTaskDialog [MFC], OnNavigatePage
- CTaskDialog [MFC], OnRadioButtonClick
- CTaskDialog [MFC], OnTimer
- CTaskDialog [MFC], OnVerificationCheckboxClick
- CTaskDialog [MFC], RemoveAllCommandControls
- CTaskDialog [MFC], RemoveAllRadioButtons
- CTaskDialog [MFC], SetCommandControlOptions
- CTaskDialog [MFC], SetCommonButtonOptions
- CTaskDialog [MFC], SetCommonButtons
- CTaskDialog [MFC], SetContent
- CTaskDialog [MFC], SetDefaultCommandControl
- CTaskDialog [MFC], SetDefaultRadioButton
- CTaskDialog [MFC], SetDialogWidth
- CTaskDialog [MFC], SetExpansionArea
- CTaskDialog [MFC], SetFooterIcon
- CTaskDialog [MFC], SetFooterText
- CTaskDialog [MFC], SetMainIcon
- CTaskDialog [MFC], SetMainInstruction
- CTaskDialog [MFC], SetOptions
- CTaskDialog [MFC], SetProgressBarMarquee
- CTaskDialog [MFC], SetProgressBarPosition
- CTaskDialog [MFC], SetProgressBarRange
- CTaskDialog [MFC], SetProgressBarState
- CTaskDialog [MFC], SetRadioButtonOptions
- CTaskDialog [MFC], SetVerificationCheckbox
- CTaskDialog [MFC], SetVerificationCheckboxText
- CTaskDialog [MFC], SetWindowTitle
- CTaskDialog [MFC], ShowDialog
- CTaskDialog [MFC], TaskDialogCallback
ms.assetid: 1991ec98-ae56-4483-958b-233809c8c559
ms.openlocfilehash: e2f77a2eda4397ed368e477165e876f9b8fbf936
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502351"
---
# <a name="ctaskdialog-class"></a>CTaskDialog Class

メッセージ ボックスのような機能を持つだけでなく、ユーザーに対する追加情報も表示できる、ポップアップ ダイアログ ボックスです。 `CTaskDialog` には、ユーザーから情報を収集するための機能も用意されています。

## <a name="syntax"></a>構文

```
class CTaskDialog : public CObject
```

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[CTaskDialog::CTaskDialog](#ctaskdialog)|`CTaskDialog` オブジェクトを構築します。|

### <a name="methods"></a>メソッド

|||
|-|-|
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|にコマンドボタンコントロールを追加し`CTaskDialog`ます。|
|[CTaskDialog::AddRadioButton](#addradiobutton)|にオプションボタンを追加し`CTaskDialog`ます。|
|[CTaskDialog:: ClickCommandControl](#clickcommandcontrol)|コマンドボタンコントロールまたは共通ボタンをプログラムでクリックします。|
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|プログラムによってオプションボタンをクリックします。|
|[CTaskDialog: oModal:D](#domodal)|「`CTaskDialog`」を表示します。|
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|使用可能な共通ボタンの数を取得します。|
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|標準の Windows ボタンを`CTaskDialog`クラスに関連付けられている共通ボタンの種類に変換します。|
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|`CTaskDialog`クラスに関連付けられている一般的なボタンの種類の1つを標準の Windows ボタンに変換します。|
|[CTaskDialog::GetOptions](#getoptions)|この`CTaskDialog`のオプションフラグを返します。|
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|選択されたコマンドボタンコントロールを返します。|
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|選択されたラジオボタンを返します。|
|[CTaskDialog:: GetVerificationCheckboxState](#getverificationcheckboxstate)|検証チェックボックスの状態を取得します。|
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|コマンドボタンコントロールまたは共通ボタンが有効かどうかを判断します。|
|[CTaskDialog:: IsRadioButtonEnabled](#isradiobuttonenabled)|オプションボタンが有効かどうかを判断します。|
|[CTaskDialog::IsSupported](#issupported)|アプリケーションを実行しているコンピューターでが`CTaskDialog`サポートされているかどうかを判断します。|
|[CTaskDialog:: LoadCommandControls](#loadcommandcontrols)|文字列テーブルのデータを使用して、コマンドボタンコントロールを追加します。|
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|文字列テーブルのデータを使用して、オプションボタンを追加します。|
|[CTaskDialog:: NavigateTo](#navigateto)|フォーカスを別`CTaskDialog`のに転送します。|
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|フレームワークは、ユーザーがコマンドボタンコントロールをクリックしたときにこのメソッドを呼び出します。|
|[CTaskDialog::OnCreate](#oncreate)|フレームワークは、を作成した後に`CTaskDialog`、このメソッドを呼び出します。|
|[CTaskDialog::OnDestroy](#ondestroy)|フレームワークは、を`CTaskDialog`破棄する直前にこのメソッドを呼び出します。|
|[CTaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|フレームワークは、ユーザーが展開ボタンをクリックしたときにこのメソッドを呼び出します。|
|[CTaskDialog::OnHelp](#onhelp)|フレームワークは、ユーザーがヘルプを要求したときにこのメソッドを呼び出します。|
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|フレームワークは、ユーザーがハイパーリンクをクリックしたときにこのメソッドを呼び出します。|
|[CTaskDialog::OnInit](#oninit)|`CTaskDialog`が初期化されると、フレームワークはこのメソッドを呼び出します。|
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|フレームワークは、 `CTaskDialog`ユーザーが上のコントロールに関してフォーカスを移動したときに、このメソッドを呼び出します。|
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|フレームワークは、ユーザーがラジオボタンコントロールを選択したときにこのメソッドを呼び出します。|
|[CTaskDialog::OnTimer](#ontimer)|フレームワークは、タイマーの有効期限が切れたときにこのメソッドを呼び出します。|
|[CTaskDialog:: OnVerificationCheckboxClick](#onverificationcheckboxclick)|フレームワークは、ユーザーが検証チェックボックスをクリックしたときにこのメソッドを呼び出します。|
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|からすべてのコマンドコントロールを削除`CTaskDialog`します。|
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|からすべてのオプションボタンを削除`CTaskDialog`します。|
|[CTaskDialog:: SetCommandControlOptions](#setcommandcontroloptions)|の`CTaskDialog`コマンドボタンコントロールを更新します。|
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|有効にする共通ボタンのサブセットを更新し、UAC による昇格を要求します。|
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|に共通ボタンを`CTaskDialog`追加します。|
|[CTaskDialog::SetContent](#setcontent)|のコンテンツを更新`CTaskDialog`します。|
|[CTaskDialog:: SetDefaultCommandControl](#setdefaultcommandcontrol)|既定のコマンドボタンコントロールを指定します。|
|[CTaskDialog:: SetDefaultRadioButton](#setdefaultradiobutton)|既定のラジオボタンを指定します。|
|[CTaskDialog::SetDialogWidth](#setdialogwidth)|の幅を調整`CTaskDialog`します。|
|[CTaskDialog:: Setの場所](#setexpansionarea)|の展開領域を更新`CTaskDialog`します。|
|[CTaskDialog:: Setフッターアイコン](#setfootericon)|のフッターアイコン`CTaskDialog`を更新します。|
|[CTaskDialog:: Setフッターテキスト](#setfootertext)|のフッターのテキストを更新`CTaskDialog`します。|
|[CTaskDialog:: SetMainIcon](#setmainicon)|のメインアイコンを更新し`CTaskDialog`ます。|
|[CTaskDialog:: SetMainInstruction](#setmaininstruction)|のメイン命令を更新し`CTaskDialog`ます。|
|[CTaskDialog::SetOptions](#setoptions)|のオプション`CTaskDialog`を構成します。|
|[CTaskDialog:: Set進捗 Barmarquee](#setprogressbarmarquee)|のマーキーバー `CTaskDialog`を構成し、それをダイアログボックスに追加します。|
|[CTaskDialog:: Setて Barposition](#setprogressbarposition)|プログレスバーの位置を調整します。|
|[CTaskDialog::SetProgressBarRange](#setprogressbarrange)|プログレスバーの範囲を調整します。|
|[CTaskDialog:: Set進捗状況 Barstate](#setprogressbarstate)|プログレスバーの状態をに設定し、 `CTaskDialog`に表示します。|
|[CTaskDialog:: SetRadioButtonOptions](#setradiobuttonoptions)|ラジオボタンを有効または無効にします。|
|[CTaskDialog:: SetVerificationCheckbox](#setverificationcheckbox)|検証チェックボックスのチェック状態を設定します。|
|[CTaskDialog:: SetVerificationCheckboxText](#setverificationcheckboxtext)|検証チェックボックスの右側にテキストを設定します。|
|[CTaskDialog:: SetWindowTitle](#setwindowtitle)|のタイトルを設定し`CTaskDialog`ます。|
|[CTaskDialog::ShowDialog](#showdialog)|を`CTaskDialog`作成して表示します。|
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|フレームワークは、さまざまな Windows メッセージに応答してこれを呼び出します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|`m_aButtons`|のコマンドボタンコントロール`CTaskDialog`の配列。|
|`m_aRadioButtons`|のオプションボタンコントロール`CTaskDialog`の配列。|
|`m_bVerified`|`TRUE`検証チェックボックスがオンになっていることを示します。`FALSE`がではないことを示します。|
|`m_footerIcon`|のフッターのアイコン`CTaskDialog`。|
|`m_hWnd`|のウィンドウ`CTaskDialog`へのハンドル。|
|`m_mainIcon`|のメインアイコン`CTaskDialog`。|
|`m_nButtonDisabled`|どの共通ボタンが無効になっているかを示すマスク。|
|`m_nButtonElevation`|UAC の昇格が必要な共通ボタンを示すマスク。|
|`m_nButtonId`|選択されたコマンドボタンコントロールの ID。|
|`m_nCommonButton`|に表示される共通ボタンを示すマスク`CTaskDialog`。|
|`m_nDefaultCommandControl`|`CTaskDialog`が表示されるときに選択されるコマンドボタンコントロールの ID。|
|`m_nDefaultRadioButton`|`CTaskDialog`が表示されるときに選択されるオプションボタンコントロールの ID。|
|`m_nFlags`|のオプション`CTaskDialog`を示すマスク。|
|`m_nProgressPos`|プログレスバーの現在の位置。  この値の有効値の範囲は `m_nProgressRangeMin` ～ `m_nProgressRangeMax` です。|
|`m_nProgressRangeMax`|プログレスバーの最大値。|
|`m_nProgressRangeMin`|プログレスバーの最小値。|
|`m_nProgressState`|プログレスバーの状態。 詳細については、「 [CTaskDialog:: setのステータスバーの状態](#setprogressbarstate)」を参照してください。|
|`m_nRadioId`|選択されたラジオボタンコントロールの ID。|
|`m_nWidth`|の幅`CTaskDialog` (ピクセル単位)。|
|`m_strCollapse`|展開され`CTaskDialog`た情報が非表示になったときに、展開ボックスの右側に表示される文字列。|
|`m_strContent`|のコンテンツ文字列`CTaskDialog`。|
|`m_strExpand`|展開され`CTaskDialog`た情報が表示されるときに、展開ボックスの右側に表示される文字列。|
|`m_strFooter`|の`CTaskDialog`フッター。|
|`m_strInformation`|の展開された`CTaskDialog`情報。|
|`m_strMainInstruction`|のメイン命令`CTaskDialog`。|
|`m_strTitle`|の`CTaskDialog`タイトル。|
|`m_strVerification`|検証チェックボックスの`CTaskDialog`右側に表示される文字列。|

## <a name="remarks"></a>Remarks

クラス`CTaskDialog`は標準の Windows メッセージボックスに代わるものであり、ユーザーから情報を収集するための新しいコントロールなどの追加機能が用意されています。 このクラスは、Visual Studio 2010 以降の MFC ライブラリにあります。 は`CTaskDialog` 、Windows Vista 以降で使用できます。 以前のバージョンの Windows では`CTaskDialog` 、オブジェクトを表示できません。 現在`CTaskDialog::IsSupported`のユーザーがタスクダイアログボックスを表示できるかどうかを実行時に決定するために使用します。 標準の Windows メッセージボックスは引き続きサポートされています。

は`CTaskDialog` 、Unicode ライブラリを使用してアプリケーションをビルドする場合にのみ使用できます。

に`CTaskDialog`は、2つの異なるコンストラクターがあります。 1つのコンストラクターを使用すると、2つのコマンドボタンと、最大6つの標準ボタンコントロールを指定できます。 を作成した後で、 `CTaskDialog`コマンドボタンを追加できます。 2番目のコンストラクターはコマンドボタンをサポートしていませんが、通常のボタンコントロールをいくつでも追加できます。 コンストラクターの詳細については、「 [ctaskdialog:: ctaskdialog](#ctaskdialog)」を参照してください。

次の図は、いくつ`CTaskDialog`かのコントロールの場所を示すサンプルを示しています。

![CTaskDialog の例](../../mfc/reference/media/ctaskdialogsample.png "CTaskDialog の例") <br/>
CTaskDialog サンプル

## <a name="requirements"></a>必要条件

**最低限必要なオペレーティングシステム:** Windows Vista

**ヘッダー:** afxtaskdialog

##  <a name="addcommandcontrol"></a>  CTaskDialog::AddCommandControl

新しいコマンドボタンコントロールをに`CTaskDialog`追加します。

```
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>パラメーター

*nCommandControlID*<br/>
からコマンド制御 id 番号。

*strCaption*<br/>
からによっ`CTaskDialog`てユーザーに表示される文字列。 この文字列を使用して、コマンドの目的を説明します。

*bEnabled*<br/>
から[新規] ボタンが有効か無効かを示すブール値のパラメーターです。

*bRequiresElevation*<br/>
からコマンドが昇格を必要とするかどうかを示すブール型パラメーターです。

### <a name="remarks"></a>Remarks

で`CTaskDialog Class`表示できるコマンドボタンコントロールの数に制限はありません。 ただし、に`CTaskDialog`コマンドボタンコントロールが表示されている場合は、最大6個のボタンを表示できます。 に`CTaskDialog`コマンドボタンコントロールがない場合、表示されるボタンの数に制限はありません。

ユーザーがコマンドボタンコントロールを選択すると、 `CTaskDialog`が閉じます。 アプリケーションで[CTaskDialog::D omodal](#domodal)を使用してダイアログボックスを表示`DoModal`すると、選択したコマンドボタンコントロールの*ncommandcontrolid*が返されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="addradiobutton"></a>  CTaskDialog::AddRadioButton

にオプションボタンを追加し`CTaskDialog`ます。

```
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>パラメーター

*nRadioButtonID*<br/>
からオプションボタンの識別番号。

*strCaption*<br/>
からがオプションボタンの`CTaskDialog`横に表示される文字列。

*bEnabled*<br/>
からオプションボタンが有効かどうかを示すブール型パラメーターです。

### <a name="remarks"></a>Remarks

[CTaskDialog クラス](../../mfc/reference/ctaskdialog-class.md)のオプションボタンを使用すると、ユーザーから情報を収集できます。 関数[CTaskDialog:: GetSelectedRadioButtonID](#getselectedradiobuttonid)を使用して、どのオプションボタンが選択されているかを判断します。

で`CTaskDialog`は、各オプションボタンに対して*nRadioButtonID*パラメーターが一意である必要はありません。 ただし、各オプションボタンに対して個別の識別子を使用しないと、予期しない動作が発生することがあります。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="clickcommandcontrol"></a>CTaskDialog:: ClickCommandControl

コマンドボタンコントロールまたは共通ボタンをプログラムでクリックします。

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>パラメーター

*nCommandControlID*<br/>
からクリックするコントロールのコマンド ID。

### <a name="remarks"></a>Remarks

このメソッドは、windows メッセージ TDM_CLICK_BUTTON を生成します。

##  <a name="clickradiobutton"></a>  CTaskDialog::ClickRadioButton

プログラムによってオプションボタンをクリックします。

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>パラメーター

*nRadioButtonID*<br/>
からクリックするオプションボタンの ID。

### <a name="remarks"></a>Remarks

このメソッドは、windows メッセージ TDM_CLICK_RADIO_BUTTON を生成します。

##  <a name="ctaskdialog"></a>  CTaskDialog::CTaskDialog

[CTaskDialog クラス](../../mfc/reference/ctaskdialog-class.md)のインスタンスを作成します。

```
CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nCommonButtons = TDCBF_OK_BUTTON | TDCBF_CANCEL_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));

CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>パラメーター

*strContent*<br/>
からのコンテンツに使用する文字列`CTaskDialog`。

*strMainInstruction*<br/>
からのメイン命令`CTaskDialog`。

*strTitle*<br/>
からの`CTaskDialog`タイトル。

*nCommonButtons*<br/>
からに追加する共通ボタンのマスク`CTaskDialog`。

*Ntaskのオプション*<br/>
からに使用`CTaskDialog`するオプションのセット。

*strFooter*<br/>
からフッターとして使用する文字列。

*nIDCommandControlsFirst*<br/>
から最初のコマンドの文字列 ID。

*nIDCommandControlsLast*<br/>
から最後のコマンドの文字列 ID。

### <a name="remarks"></a>Remarks

アプリケーションにを追加するには、 `CTaskDialog`次の2つの方法があります。 最初の方法では、コンストラクターの1つを使用し`CTaskDialog`てを作成し、 [CTaskDialog::D omodal](#domodal)を使用して表示します。 2番目の方法では、静的関数[CTaskDialog:: ShowDialog](#showdialog)を使用します。これ`CTaskDialog`により、オブジェクト`CTaskDialog`を明示的に作成せずにを表示できます。

2番目のコンストラクターは、アプリケーションのリソースファイルからのデータを使用して、コマンドボタンコントロールを作成します。 リソースファイル内の文字列テーブルには、文字列 Id が関連付けられた複数の文字列があります。 このメソッドは、NIDCommandControlsFirst と*Ncommand*の間の文字列テーブル内の有効な各エントリに対して、コマンドボタンコントロールを追加します。 これらのコマンドボタンコントロールでは、文字列テーブル内の文字列はコントロールのキャプションで、文字列 ID はコントロールの ID です。

有効なオプションの一覧については、「 [CTaskDialog:: SetOptions](#setoptions) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="domodal"></a>CTaskDialog: oModal:D

を表示`CTaskDialog`し、モーダルにします。

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>パラメーター

*hParent*<br/>
からの親ウィンドウ`CTaskDialog`。

### <a name="return-value"></a>戻り値

ユーザーが選択した項目に対応する整数。

### <a name="remarks"></a>Remarks

[CTaskDialog](../../mfc/reference/ctaskdialog-class.md)のこのインスタンスを表示します。 アプリケーションは、ユーザーがダイアログボックスを閉じるまで待機します。

は`CTaskDialog` 、ユーザーが共通ボタンまたはコマンドリンクコントロールを選択したとき、また`CTaskDialog`はを閉じると閉じます。 戻り値は、ユーザーがダイアログボックスを閉じた方法を示す識別子です。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="getcommonbuttoncount"></a>  CTaskDialog::GetCommonButtonCount

共通ボタンの数を取得します。

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>戻り値

使用可能な共通ボタンの数。

### <a name="remarks"></a>Remarks

一般的なボタンは、 [ctaskdialog:: ctaskdialog](#ctaskdialog)に指定する既定のボタンです。 [CTaskDialog クラス](../../mfc/reference/ctaskdialog-class.md)は、ダイアログボックスの下部にあるボタンを表示します。

列挙されたボタンの一覧は、CommCtrl. h にあります。

##  <a name="getcommonbuttonflag"></a>  CTaskDialog::GetCommonButtonFlag

標準の Windows ボタンを、 [CTaskDialog クラス](../../mfc/reference/ctaskdialog-class.md)に関連付けられている共通ボタンの種類に変換します。

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>パラメーター

*nButtonId*<br/>
から標準の Windows ボタンの値。

### <a name="return-value"></a>戻り値

対応する`CTaskDialog`共通ボタンの値。 対応する共通ボタンがない場合、このメソッドは0を返します。

##  <a name="getcommonbuttonid"></a>  CTaskDialog::GetCommonButtonId

[CTaskDialog クラス](../../mfc/reference/ctaskdialog-class.md)に関連付けられている一般的なボタンの種類の1つを標準の Windows ボタンに変換します。

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>パラメーター

*n*<br/>
から`CTaskDialog`クラスに関連付けられている共通ボタンの種類。

### <a name="return-value"></a>戻り値

対応する標準の Windows ボタンの値。 対応する Windows ボタンがない場合、メソッドは0を返します。

##  <a name="getoptions"></a>  CTaskDialog::GetOptions

この`CTaskDialog`のオプションフラグを返します。

```
int GetOptions() const;
```

### <a name="return-value"></a>戻り値

のフラグ`CTaskDialog`。

### <a name="remarks"></a>Remarks

[Ctaskdialog クラス](../../mfc/reference/ctaskdialog-class.md)で使用できるオプションの詳細については、「 [Ctaskdialog:: SetOptions](#setoptions)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="getselectedcommandcontrolid"></a>  CTaskDialog::GetSelectedCommandControlID

選択されたコマンドボタンコントロールを返します。

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>戻り値

現在選択されているコマンドボタンコントロールの ID。

### <a name="remarks"></a>Remarks

このメソッドを使用して、ユーザーが選択したコマンドボタンの ID を取得する必要はありません。 この ID は、 [ctaskdialog::D oModal](#domodal)または[Ctaskdialog:: ShowDialog](#showdialog)によって返されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="getselectedradiobuttonid"></a>CTaskDialog:: GetSelectedRadioButtonID

選択されたラジオボタンを返します。

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>戻り値

選択されたラジオボタンの ID です。

### <a name="remarks"></a>Remarks

このメソッドは、ユーザーがダイアログボックスを閉じた後に、選択したラジオボタンを取得するために使用できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="getverificationcheckboxstate"></a>CTaskDialog:: GetVerificationCheckboxState

検証チェックボックスの状態を取得します。

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>戻り値

チェックボックスがオンになっている場合は TRUE、それ以外の場合は FALSE。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="iscommandcontrolenabled"></a>  CTaskDialog::IsCommandControlEnabled

コマンドボタンコントロールまたはボタンが有効かどうかを判断します。

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>パラメーター

*nCommandControlID*<br/>
からテストするコマンドボタンコントロールまたはボタンの ID。

### <a name="return-value"></a>戻り値

コントロールが有効な場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドを使用すると、コマンドボタンコントロールと`CTaskDialog`クラス * の共通ボタンの両方が使用可能かどうかを判断できます。

*Ncommandcontrolid*が、共通`CTaskDialog`ボタンまたはコマンドボタンコントロールの有効な識別子ではない場合、このメソッドは例外をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="isradiobuttonenabled"></a>  CTaskDialog::IsRadioButtonEnabled

オプションボタンが有効かどうかを判断します。

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>パラメーター

*nRadioButtonID*<br/>
からテストするオプションボタンの ID。

### <a name="return-value"></a>戻り値

オプションボタンが有効になっている場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

*NRadioButtonID*がオプションボタンの有効な識別子ではない場合、このメソッドは例外をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="issupported"></a>  CTaskDialog::IsSupported

アプリケーションを実行しているコンピューターでが`CTaskDialog`サポートされているかどうかを判断します。

```
static BOOL IsSupported();
```

### <a name="return-value"></a>戻り値

コンピューターでがサポートされ`CTaskDialog`ている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

アプリケーションを実行しているコンピューターでクラスが`CTaskDialog`サポートされている場合は、実行時にこの関数を使用して判断します。 コンピューターでが`CTaskDialog`サポートされていない場合は、別の方法でユーザーに情報を伝える必要があります。 クラスをサポートし`CTaskDialog` `CTaskDialog`ていないコンピューターでを使用しようとすると、アプリケーションがクラッシュします。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="loadcommandcontrols"></a>  CTaskDialog::LoadCommandControls

文字列テーブルのデータを使用して、コマンドボタンコントロールを追加します。

```
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>パラメーター

*nIDCommandControlsFirst*<br/>
から最初のコマンドの文字列 ID。

*nIDCommandControlsLast*<br/>
から最後のコマンドの文字列 ID。

### <a name="remarks"></a>Remarks

このメソッドは、アプリケーションのリソースファイルからのデータを使用して、コマンドボタンコントロールを作成します。 リソースファイル内の文字列テーブルには、文字列 Id が関連付けられた複数の文字列があります。 このメソッドを使用して追加された新しいコマンドボタンコントロールは、コントロールのキャプションに文字列を、コントロールの ID に文字列 ID を使用します。 選択された文字列の範囲は、 *nIDCommandControlsFirst と* *ncommand*によって指定されます。 範囲内に空のエントリがある場合、メソッドはそのエントリのコマンドボタンコントロールを追加しません。

既定では、新しいコマンドボタンコントロールが有効になり、昇格は必要ありません。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="loadradiobuttons"></a>  CTaskDialog::LoadRadioButtons

文字列テーブルのデータを使用して、オプションボタンコントロールを追加します。

```
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>パラメーター

*nIDRadioButtonsFirst*<br/>
から最初のオプションボタンの文字列 ID。

*nIDRadioButtonsLast*<br/>
から最後のオプションボタンの文字列 ID。

### <a name="remarks"></a>Remarks

このメソッドは、アプリケーションのリソースファイルからのデータを使用して、オプションボタンを作成します。 リソースファイル内の文字列テーブルには、文字列 Id が関連付けられた複数の文字列があります。 このメソッドを使用して追加された新しいラジオボタンは、ラジオボタンのキャプションに文字列を使用し、ラジオボタンの ID に文字列 ID を使用します。 選択された文字列の範囲は、 *nIDRadioButtonsFirst*および*nRadioButtonsLast*によって指定されます。 範囲内に空のエントリがある場合、メソッドはそのエントリに対してオプションボタンを追加しません。

既定では、新しいオプションボタンが有効になっています。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="navigateto"></a>CTaskDialog:: NavigateTo

フォーカスを別`CTaskDialog`のに転送します。

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>パラメーター

*oTaskDialog*<br/>
から`CTaskDialog`フォーカスを受け取る。

### <a name="remarks"></a>Remarks

このメソッドは、 `CTaskDialog` *otaskdialog*を表示するときに、現在のを非表示にします。 *Otaskdialog*は、現在`CTaskDialog`のと同じ場所に表示されます。

##  <a name="oncommandcontrolclick"></a>CTaskDialog:: OnCommandControlClick

フレームワークは、ユーザーがコマンドボタンコントロールをクリックしたときにこのメソッドを呼び出します。

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>パラメーター

*nCommandControlID*<br/>
からユーザーが選択したコマンドボタンコントロールの ID。

### <a name="return-value"></a>戻り値

既定の実装では、S_OK が返されます。

### <a name="remarks"></a>Remarks

派生クラスでこのメソッドをオーバーライドして、カスタム動作を実装します。

##  <a name="oncreate"></a>  CTaskDialog::OnCreate

フレームワークは、を作成した後に`CTaskDialog`、このメソッドを呼び出します。

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>戻り値

既定の実装では、S_OK が返されます。

### <a name="remarks"></a>Remarks

派生クラスでこのメソッドをオーバーライドして、カスタム動作を実装します。

##  <a name="ondestroy"></a>  CTaskDialog::OnDestroy

フレームワークは、を`CTaskDialog`破棄する直前にこのメソッドを呼び出します。

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>戻り値

既定の実装では、S_OK が返されます。

### <a name="remarks"></a>Remarks

派生クラスでこのメソッドをオーバーライドして、カスタム動作を実装します。

##  <a name="onexpandbuttonclick"></a>CTaskDialog:: OnExpandButtonClick

フレームワークは、ユーザーが展開ボタンをクリックしたときにこのメソッドを呼び出します。

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>パラメーター

*bExpanded*<br/>
から0以外の値は、追加情報が表示されることを示します。0は、追加情報が非表示であることを示します。

### <a name="return-value"></a>戻り値

既定の実装では、S_OK が返されます。

### <a name="remarks"></a>Remarks

派生クラスでこのメソッドをオーバーライドして、カスタム動作を実装します。

##  <a name="onhelp"></a>  CTaskDialog::OnHelp

フレームワークは、ユーザーがヘルプを要求したときにこのメソッドを呼び出します。

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>戻り値

既定の実装では、S_OK が返されます。

### <a name="remarks"></a>Remarks

派生クラスでこのメソッドをオーバーライドして、カスタム動作を実装します。

##  <a name="onhyperlinkclick"></a>  CTaskDialog::OnHyperlinkClick

フレームワークは、ユーザーがハイパーリンクをクリックしたときにこのメソッドを呼び出します。

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>パラメーター

*strHref*<br/>
からハイパーリンクを表す文字列。

### <a name="return-value"></a>戻り値

既定の実装では、S_OK が返されます。

### <a name="remarks"></a>Remarks

このメソッドは、S_OK を返す前に、 [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew)を呼び出します。

派生クラスでこのメソッドをオーバーライドして、カスタム動作を実装します。

##  <a name="oninit"></a>  CTaskDialog::OnInit

`CTaskDialog`が初期化されると、フレームワークはこのメソッドを呼び出します。

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>戻り値

既定の実装では、S_OK が返されます。

### <a name="remarks"></a>Remarks

派生クラスでこのメソッドをオーバーライドして、カスタム動作を実装します。

##  <a name="onnavigatepage"></a>  CTaskDialog::OnNavigatePage

フレームワークは、 [CTaskDialog:: NavigateTo](#navigateto)メソッドに応答してこのメソッドを呼び出します。

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>戻り値

既定の実装では、S_OK が返されます。

### <a name="remarks"></a>Remarks

派生クラスでこのメソッドをオーバーライドして、カスタム動作を実装します。

##  <a name="onradiobuttonclick"></a>  CTaskDialog::OnRadioButtonClick

フレームワークは、ユーザーがラジオボタンコントロールを選択したときにこのメソッドを呼び出します。

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>パラメーター

*nRadioButtonID*<br/>
からユーザーがクリックしたオプションボタンコントロールの ID。

### <a name="return-value"></a>戻り値

既定の実装では、S_OK が返されます。

### <a name="remarks"></a>Remarks

派生クラスでこのメソッドをオーバーライドして、カスタム動作を実装します。

##  <a name="ontimer"></a>  CTaskDialog::OnTimer

フレームワークは、タイマーの有効期限が切れたときにこのメソッドを呼び出します。

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>パラメーター

*lTime*<br/>
からが作成されて`CTaskDialog`から、またはタイマーがリセットされてからの経過時間 (ミリ秒)。

### <a name="return-value"></a>戻り値

既定の実装では、S_OK が返されます。

### <a name="remarks"></a>Remarks

派生クラスでこのメソッドをオーバーライドして、カスタム動作を実装します。

##  <a name="onverificationcheckboxclick"></a>CTaskDialog:: OnVerificationCheckboxClick

フレームワークは、ユーザーが検証チェックボックスをクリックしたときにこのメソッドを呼び出します。

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>パラメーター

*bChecked*<br/>
から[検証] チェックボックスがオンになっていることを示します。FALSE は、ではないことを示します。

### <a name="return-value"></a>戻り値

既定の実装では、S_OK が返されます。

### <a name="remarks"></a>Remarks

派生クラスでこのメソッドをオーバーライドして、カスタム動作を実装します。

##  <a name="removeallcommandcontrols"></a>  CTaskDialog::RemoveAllCommandControls

からすべてのコマンドボタンコントロールを削除`CTaskDialog`します。

```
void RemoveAllCommandControls();
```

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="removeallradiobuttons"></a>  CTaskDialog::RemoveAllRadioButtons

からすべてのオプションボタンを削除`CTaskDialog`します。

```
void RemoveAllRadioButtons();
```

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setcommandcontroloptions"></a>  CTaskDialog::SetCommandControlOptions

の`CTaskDialog`コマンドボタンコントロールを更新します。

```
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>パラメーター

*nCommandControlID*<br/>
から更新するコマンドコントロールの ID。

*bEnabled*<br/>
から指定したコマンドボタンコントロールが有効か無効かを示すブール型パラメーター。

*bRequiresElevation*<br/>
から指定されたコマンドボタンコントロールが昇格を必要とするかどうかを示すブール型パラメーター。

### <a name="remarks"></a>Remarks

このメソッドは、コマンドボタンコントロールが有効であるか、または`CTaskDialog`クラスに追加された後に昇格が必要かどうかを変更するために使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setcommonbuttonoptions"></a>  CTaskDialog::SetCommonButtonOptions

有効にする共通ボタンのサブセットを更新し、UAC による昇格を要求します。

```
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>パラメーター

*nDisabledButtonMask*<br/>
から無効にする共通ボタンのマスク。

*nElevationButtonMask*<br/>
から昇格が必要な共通ボタンのマスク。

### <a name="remarks"></a>Remarks

Ctaskdialog[クラス](../../mfc/reference/ctaskdialog-class.md)のインスタンスで使用できる共通ボタンを設定するには、「 [CTaskDialog:: ctaskdialog](#ctaskdialog) 」と「 [Ctaskdialog:: setcommonbuttons](#setcommonbuttons)」というコンストラクターを使用します。 `CTaskDialog::SetCommonButtonOptions`では、新しい共通ボタンの追加はサポートされていません。

このメソッドを使用して、この`CTaskDialog`では使用できない共通ボタンを無効または昇格する場合、このメソッドは、[保証](diagnostic-services.md#ensure)マクロを使用して例外をスローします。

このメソッドは、 `CTaskDialog`で使用可能なすべてのボタンを有効にしますが、以前に無効になっていた場合でも、 *nDisabledButtonMask*には含まれません。 このメソッドは、昇格を同様の方法で処理します。共通ボタンが使用可能であっても、 *nElevationButtonMask*に含まれていない場合は、一般的なボタンが表示されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcommonbuttons"></a>  CTaskDialog::SetCommonButtons

に共通ボタンを`CTaskDialog`追加します。

```
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>パラメーター

*nButtonMask*<br/>
からに追加するボタンのマスク`CTaskDialog`。

*nDisabledButtonMask*<br/>
から無効にするボタンのマスク。

*nElevationButtonMask*<br/>
から昇格が必要なボタンのマスク。

### <a name="remarks"></a>Remarks

`CTaskDialog`クラスのこのインスタンスの表示ウィンドウが作成された後に、このメソッドを呼び出すことはできません。 このメソッドを実行すると、例外がスローされます。

*Nbuttonmask*によって示されるボタンは、 `CTaskDialog`以前にに追加された共通ボタンをオーバーライドします。 *Nbuttonmask*に示されているボタンのみ使用できます。

*NDisabledButtonMask*または*NElevationButtonMask*に*nbuttonmask*にないボタンが含まれている場合、このメソッドは、[保証](diagnostic-services.md#ensure)マクロを使用して例外をスローします。

既定では、すべての共通ボタンが有効になり、昇格は必要ありません。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcontent"></a>  CTaskDialog::SetContent

のコンテンツを更新`CTaskDialog`します。

```
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>パラメーター

*strContent*<br/>
からユーザーに表示する文字列。

### <a name="remarks"></a>Remarks

`CTaskDialog`クラスの内容は、ダイアログボックスのメインセクションでユーザーに表示されるテキストです。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setdefaultcommandcontrol"></a>  CTaskDialog::SetDefaultCommandControl

既定のコマンドボタンコントロールを指定します。

```
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>パラメーター

*nCommandControlID*<br/>
から既定のコマンドボタンコントロールの ID。

### <a name="remarks"></a>Remarks

既定のコマンドボタンコントロールは、 `CTaskDialog`が最初にユーザーに表示されるときに選択されるコントロールです。

*Ncommandcontrolid*によって指定されたコマンドボタンコントロールが見つからない場合、このメソッドは例外をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setdefaultradiobutton"></a>CTaskDialog:: SetDefaultRadioButton

既定のラジオボタンを指定します。

```
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>パラメーター

*nRadioButtonID*<br/>
から既定値となるオプションボタンの ID。

### <a name="remarks"></a>Remarks

既定のオプションボタンは、 `CTaskDialog`が最初にユーザーに表示されるときに選択されるボタンです。

*NRadioButtonID*によって指定されたオプションボタンが見つからない場合、このメソッドは例外をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setdialogwidth"></a>  CTaskDialog::SetDialogWidth

の幅を調整`CTaskDialog`します。

```
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>パラメーター

*nWidth*<br/>
からダイアログボックスの幅 (ピクセル単位)。

### <a name="remarks"></a>Remarks

パラメーター *nWidth*は0以上である必要があります。 それ以外の場合、このメソッドは例外をスローします。

*NWidth*が0に設定されている場合、このメソッドはダイアログボックスを既定のサイズに設定します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setexpansionarea"></a>CTaskDialog:: Setの場所

の展開領域を更新`CTaskDialog`します。

```
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>パラメーター

*strExpandedInformation*<br/>
からユーザーが展開ボタン`CTaskDialog`をクリックしたときに、ダイアログボックスの本体に表示される文字列。

*strCollapsedLabel*<br/>
から展開された`CTaskDialog`領域が折りたたまれたときに、展開ボタンの横に表示される文字列。

*strExpandedLabel*<br/>
から展開された`CTaskDialog`領域が表示されるときに、展開ボタンの横に表示される文字列。

### <a name="remarks"></a>Remarks

`CTaskDialog`クラスの展開領域を使用すると、ユーザーに追加情報を提供できます。 展開領域はのメイン部分`CTaskDialog`にあり、タイトルとコンテンツ文字列のすぐ下に配置されます。

が最初に表示されるときは、展開された情報が`strCollapsedLabel`表示されず、展開ボタンの横に配置されます。 `CTaskDialog` ユーザーが展開ボタン`CTaskDialog`をクリックすると、 *strexpandedinformation*が表示され、ラベルが*strexpandedinformation*に変わります。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootericon"></a>  CTaskDialog::SetFooterIcon

のフッターアイコンを更新し`CTaskDialog`ます。

```
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>パラメーター

*Hフッターアイコン*<br/>
からの新しいアイコン`CTaskDialog`。

*lpszFooterIcon*<br/>
からの新しいアイコン`CTaskDialog`。

### <a name="remarks"></a>Remarks

[CTaskDialog クラス](../../mfc/reference/ctaskdialog-class.md)の下部にフッターアイコンが表示されます。 これには、関連付けられたフッターテキストを含めることができます。 このフッターテキストは、 [CTaskDialog:: Setfooter text](#setfootertext)で変更できます。

`CTaskDialog`が表示された場合、または入力パラメーターが NULL の場合、このメソッドは、[保証](diagnostic-services.md#ensure)マクロで例外をスローします。

で`CTaskDialog` `HICON`は、または`LPCWSTR`をフッターアイコンとしてのみ使用できます。 これを構成するには、コンストラクターでオプション TDF_USE_HICON_FOOTER を設定するか、または[CTaskDialog:: SetOptions](#setoptions)を設定します。 既定では、 `CTaskDialog`は、フッターアイコン`LPCWSTR`の入力の種類としてを使用するように構成されています。 このメソッドは、不適切な型を使用してアイコンを設定しようとすると、例外を生成します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootertext"></a>  CTaskDialog::SetFooterText

のフッターのテキストを更新`CTaskDialog`します。

```
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>パラメーター

*strFooterText*<br/>
からフッターの新しいテキスト。

### <a name="remarks"></a>Remarks

の下部にあるフッターのテキストの横に、フッターアイコンが`CTaskDialog`表示されます。 [ [CTaskDialog:: Setfooter] アイコン](#setfootericon)を使用して、フッターアイコンを変更できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmainicon"></a>CTaskDialog:: SetMainIcon

のメインアイコンを更新し`CTaskDialog`ます。

```
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>パラメーター

*hMainIcon*<br/>
から新しいアイコン。

*lpszMainIcon*<br/>
から新しいアイコン。

### <a name="remarks"></a>Remarks

`CTaskDialog`が表示された場合、または入力パラメーターが NULL の場合、このメソッドは、[保証](diagnostic-services.md#ensure)マクロで例外をスローします。

は、メインアイコンと`HICON`し`LPCWSTR`てまたはのみを受け入れることができます。`CTaskDialog` これを構成するには、コンストラクターまたは[CTaskDialog:: SetOptions](#setoptions)メソッドで TDF_USE_HICON_MAIN オプションを設定します。 既定では、 `CTaskDialog`はメインアイコンの`LPCWSTR`入力の種類としてを使用するように構成されています。 このメソッドは、不適切な型を使用してアイコンを設定しようとすると、例外を生成します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmaininstruction"></a>CTaskDialog:: SetMainInstruction

のメイン命令を更新し`CTaskDialog`ます。

```
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>パラメーター

*strInstructions*<br/>
から新しいメイン命令。

### <a name="remarks"></a>Remarks

`CTaskDialog`クラスの主要な命令は、大きな太字のフォントでユーザーに表示されるテキストです。 これは、タイトルバーの下のダイアログボックスにあります。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setoptions"></a>  CTaskDialog::SetOptions

のオプション`CTaskDialog`を構成します。

```
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>パラメーター

*nOptionFlag*<br/>
からに使用`CTaskDialog`するフラグのセット。

### <a name="remarks"></a>Remarks

このメソッドは、 `CTaskDialog`の現在のすべてのオプションをクリアします。 現在のオプションを保持するには、最初に[CTaskDialog:: GetOptions](#getoptions)を使用してこれらのオプションを取得し、設定するオプションと結合する必要があります。

次の表に、すべての有効なオプションを示します。

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|でハイパーリンクを`CTaskDialog`有効にします。|
|TDF_USE_HICON_MAIN|メインアイコンにを`HICON`使用するようにを構成します。`CTaskDialog` 別の方法として`LPCWSTR`、を使用する方法があります。|
|TDF_USE_HICON_FOOTER|フッターアイコンにを`HICON`使用するようにを構成します。`CTaskDialog` 別の方法として`LPCWSTR`、を使用する方法があります。|
|TDF_ALLOW_DIALOG_CANCELLATION|**[キャンセル**] ボタンが有効`CTaskDialog`になっていない場合でも、ユーザーがキーボードを使用して、またはダイアログボックスの右上隅にあるアイコンを使用して、を閉じることができるようにします。 このフラグが設定されておらず、 **[キャンセル**] ボタンが有効になっていない場合、ユーザーは Alt + F4、esc キー、またはタイトルバーの [閉じる] ボタンを使用してダイアログボックスを閉じることはできません。|
|TDF_USE_COMMAND_LINKS|コマンドボタンコントロールを使用するようにを構成します。 `CTaskDialog`|
|TDF_USE_COMMAND_LINKS_NO_ICON|コントロールの`CTaskDialog`横にアイコンを表示せずに、コマンドボタンコントロールを使用するようにを構成します。 TDF_USE_COMMAND_LINKS は TDF_USE_COMMAND_LINKS_NO_ICON をオーバーライドします。|
|TDF_EXPAND_FOOTER_AREA|展開領域が現在展開されていることを示します。|
|TDF_EXPANDED_BY_DEFAULT|展開領域を既定で展開するかどうかを決定します。|
|TDF_VERIFICATION_FLAG_CHECKED|検証チェックボックスが現在選択されていることを示します。|
|TDF_SHOW_PROGRESS_BAR|進行状況`CTaskDialog`バーを表示するようにを構成します。|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|プログレスバーをマーキープログレスバーとして構成します。 このオプションを有効にした場合、予期される動作を行うように TDF_SHOW_PROGRESS_BAR を設定する必要があります。|
|TDF_CALLBACK_TIMER|`CTaskDialog`コールバック間隔が約200ミリ秒に設定されていることを示します。|
|TDF_POSITION_RELATIVE_TO_WINDOW|親ウィンドウ`CTaskDialog`を基準としてを中央揃えにするようにを構成します。 このフラグが有効になっ`CTaskDialog`ていない場合、はモニターに対して相対的に中央揃えになります。|
|TDF_RTL_LAYOUT|右から左へ記述する読み取りレイアウト用にを構成します。`CTaskDialog`|
|TDF_NO_DEFAULT_RADIO_BUTTON|が表示されたときに、 `CTaskDialog`オプションボタンが選択されていないことを示します。|
|TDF_CAN_BE_MINIMIZED|ユーザーがを最小化`CTaskDialog`できるようにします。 このオプションをサポートするに`CTaskDialog`は、をモーダルにすることはできません。 Mfc ではモードレス`CTaskDialog`がサポートされていないため、mfc ではこのオプションをサポートしていません。|

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setprogressbarmarquee"></a>  CTaskDialog::SetProgressBarMarquee

のマーキーバー `CTaskDialog`を構成し、それをダイアログボックスに追加します。

```
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>パラメーター

*bEnabled*<br/>
からマーキーバーを有効にする場合は TRUE。マーキーバーを無効にしてから削除する場合`CTaskDialog`は FALSE。

*nMarqueeSpeed*<br/>
からマーキーバーの速度を示す整数。

### <a name="remarks"></a>Remarks

`CTaskDialog`クラスのメインテキストの下に、マーキーバーが表示されます。

*NMarqueeSpeed*を使用して、マーキーバーの速度を設定します。値が大きいほど低速であることを示します。 *NMarqueeSpeed*の値を0に設定すると、マーキーバーは Windows の既定の速度で移動します。

*NMarqueeSpeed*が0未満の場合、このメソッドは、[保証](diagnostic-services.md#ensure)マクロで例外をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarposition"></a>CTaskDialog:: Setて Barposition

プログレスバーの位置を調整します。

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>パラメーター

*N進行 Spos*<br/>
からプログレスバーの位置。

### <a name="remarks"></a>Remarks

*Nprogress Spos*が進行状況バーの範囲内にない場合、このメソッドは、[保証](diagnostic-services.md#ensure)マクロで例外をスローします。 [「CTaskDialog:: setprogress Barrange](#setprogressbarrange)」で進行状況バーの範囲を変更できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarrange"></a>  CTaskDialog::SetProgressBarRange

プログレスバーの範囲を調整します。

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>パラメーター

*nRangeMin*<br/>
からプログレスバーの下限。

*nRangeMax*<br/>
からプログレスバーの上限。

### <a name="remarks"></a>Remarks

プログレスバーの位置は、 *nRangeMin*と*nRangeMax*を基準にしています。 たとえば、 *nRangeMin*が50で*nRangeMax*が100の場合、75の位置はプログレスバーの半分になります。 [CTaskDialog:: setprogress Barposition](#setprogressbarposition)を使用して、進行状況バーの位置を設定します。

進行状況バーを表示するには、オプション TDF_SHOW_PROGRESS_BAR を有効にし、TDF_SHOW_MARQUEE_PROGRESS_BAR を有効にしないようにする必要があります。 このメソッドは、自動的に TDF_SHOW_PROGRESS_BAR を設定し、TDF_SHOW_MARQUEE_PROGRESS_BAR をクリアします。 Ctaskdialog[クラス](../../mfc/reference/ctaskdialog-class.md)のこのインスタンスのオプションを手動で変更するには、 [Ctaskdialog:: SetOptions](#setoptions)を使用します。

このメソッドは、 *nRangeMin*が*nRangeMax*未満でない場合に、[必ず](diagnostic-services.md#ensure)マクロを使用して例外をスローします。 このメソッドは、が既に表示`CTaskDialog`されていて、マーキープログレスバーがある場合にも例外をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarstate"></a>  CTaskDialog::SetProgressBarState

プログレスバーの状態をに設定し、 `CTaskDialog`に表示します。

```
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>パラメーター

*nState*<br/>
からプログレスバーの状態。 有効な値については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

このメソッドは、が既に表示されて`CTaskDialog`いて、マーキープログレスバーがある[場合、このマクロを](diagnostic-services.md#ensure)使用して例外をスローします。

次の表に、 *nState*で使用できる値を示します。 これらのすべての場合、進行状況バーは、指定された停止位置に到達するまで通常の色で塗りつぶされます。 その時点で、状態に基づいて色が変更されます。

|||
|-|-|
|PBST_NORMAL|プログレスバーがいっぱいになると`CTaskDialog` 、はバーの色を変更しません。 既定では、通常の色は緑です。|
|PBST_ERROR|プログレスバーがいっぱいになると`CTaskDialog` 、はバーの色をエラーの色に変更します。 既定では、赤になります。|
|PBST_PAUSED|プログレスバーがいっぱいになると`CTaskDialog` 、はバーの色を一時停止色に変更します。 既定値は黄色です。|

[CTaskDialog:: setprogress Barposition](#setprogressbarposition)を使用して、進行状況バーを停止する場所を設定できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setradiobuttonoptions"></a>CTaskDialog:: SetRadioButtonOptions

ラジオボタンを有効または無効にします。

```
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>パラメーター

*nRadioButtonID*<br/>
からオプションボタンコントロールの ID。

*bEnabled*<br/>
からオプションボタンを有効にする場合は TRUE。オプションボタンを無効にする場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、 *nRadioButtonID*がラジオボタンの有効な ID でない場合に、[必ず](diagnostic-services.md#ensure)マクロを使用して例外をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setverificationcheckbox"></a>CTaskDialog:: SetVerificationCheckbox

検証チェックボックスのチェック状態を設定します。

```
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>パラメーター

*bChecked*<br/>
からを表示するときに検証チェックボックスをオン`CTaskDialog`にする場合は TRUE。`CTaskDialog`が表示されたときに検証チェックボックスをオフにする場合は FALSE。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setverificationcheckboxtext"></a>CTaskDialog:: SetVerificationCheckboxText

検証チェックボックスの右側に表示されるテキストを設定します。

```
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>パラメーター

*strVerificationText*<br/>
からこのメソッドが検証チェックボックスの横に表示するテキスト。

### <a name="remarks"></a>Remarks

このメソッドは、 `CTaskDialog`クラスのこのインスタンスが既に表示されている場合に、[必ず](diagnostic-services.md#ensure)マクロを使用して例外をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setwindowtitle"></a>CTaskDialog:: SetWindowTitle

のタイトルを設定し`CTaskDialog`ます。

```
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>パラメーター

*strWindowTitle*<br/>
からの新しいタイトル`CTaskDialog`。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="showdialog"></a>  CTaskDialog::ShowDialog

を`CTaskDialog`作成して表示します。

```
static INT_PTR ShowDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons = TDCBF_YES_BUTTON | TDCBF_NO_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>パラメーター

*strContent*<br/>
からのコンテンツに使用する文字列`CTaskDialog`。

*strMainInstruction*<br/>
からのメイン命令`CTaskDialog`。

*strTitle*<br/>
からの`CTaskDialog`タイトル。

*nIDCommandControlsFirst*<br/>
から最初のコマンドの文字列 ID。

*nIDCommandControlsLast*<br/>
から最後のコマンドの文字列 ID。

*nCommonButtons*<br/>
からに追加するボタンのマスク`CTaskDialog`。

*Ntaskのオプション*<br/>
からに使用`CTaskDialog`するオプションのセット。

*strFooter*<br/>
からフッターとして使用する文字列。

### <a name="return-value"></a>戻り値

ユーザーが選択した項目に対応する整数。

### <a name="remarks"></a>Remarks

この静的メソッドを使用すると、コード内に`CTaskDialog`オブジェクトを`CTaskDialog`明示的に作成せずに、クラスのインスタンスを作成できます。 `CTaskDialog`オブジェクトが存在しないため、 `CTaskDialog`このメソッドを使用してを`CTaskDialog`ユーザーに表示する場合は、の他のメソッドを呼び出すことはできません。

このメソッドは、アプリケーションのリソースファイルからのデータを使用して、コマンドボタンコントロールを作成します。 リソースファイル内の文字列テーブルには、文字列 Id が関連付けられた複数の文字列があります。 このメソッドは、NIDCommandControlsFirst と*Ncommand*の間の文字列テーブル内の有効な各エントリに対して、コマンドボタンコントロールを追加します。 これらのコマンドボタンコントロールでは、文字列テーブル内の文字列はコントロールのキャプションで、文字列 ID はコントロールの ID です。

有効なオプションの一覧については、「 [CTaskDialog:: SetOptions](#setoptions) 」を参照してください。

は`CTaskDialog` 、ユーザーが共通ボタンまたはコマンドリンクコントロールを選択したとき、また`CTaskDialog`はを閉じると閉じます。 戻り値は、ユーザーがダイアログボックスを閉じた方法を示す識別子です。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="taskdialogcallback"></a>  CTaskDialog::TaskDialogCallback

フレームワークは、さまざまな Windows メッセージに応答してこのメソッドを呼び出します。

```
friend:
HRESULT TaskDialogCallback(
    HWND hWnd,
    UINT uNotification,
    WPARAM wParam,
    LPARAM lParam,
    LONG_PTR dwRefData);
```

### <a name="parameters"></a>パラメーター

*hwnd*<br/>
からの`m_hWnd`構造体`CTaskDialog`へのハンドル。

*uNotification*<br/>
から生成されたメッセージを指定する通知コード。

*wParam*<br/>
からメッセージに関する詳細情報。

*lParam*<br/>
からメッセージに関する詳細情報。

*dwRefData*<br/>
からコールバックメッセージが`CTaskDialog`適用されるオブジェクトへのポインター。

### <a name="return-value"></a>戻り値

特定の通知コードに依存します。 詳細については、次の「解説」を参照してください。

### <a name="remarks"></a>Remarks

の既定の`TaskDialogCallback`実装では、特定のメッセージが処理された後、 [CTaskDialog クラス](../../mfc/reference/ctaskdialog-class.md)の適切な On メソッドが呼び出されます。 たとえば、TDN_BUTTON_CLICKED メッセージに対する応答として`TaskDialogCallback` 、は[CTaskDialog:: oncommandcontrolclick](#oncommandcontrolclick)を呼び出します。

*WParam*および*lParam*の値は、生成された特定のメッセージによって異なります。 これらの値のいずれかまたは両方を空にすることができます。 次の表に、サポートされている既定の通知と、 *wParam*と*lParam*の値の意味を示します。 派生クラスでこのメソッドをオーバーライドする場合は、次の表の各メッセージに対してコールバックコードを実装する必要があります。

|通知メッセージ|*wParam*数値|*lParam*数値|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|使用しません。|使用しません。|
|TDN_NAVIGATED|使用しません。|使用しません。|
|TDN_BUTTON_CLICKED|コマンドボタンコントロール ID。|使用しません。|
|TDN_HYPERLINK_CLICKED|使用しません。|リンクを格納している[LPCWSTR](/windows/win32/WinProg/windows-data-types)構造体。|
|TDN_TIMER|が作成されて`CTaskDialog`から、またはタイマーがリセットされてからの経過時間 (ミリ秒)。|使用しません。|
|TDN_DESTROYED|使用しません。|使用しません。|
|TDN_RADIO_BUTTON_CLICKED|ラジオボタン ID。|使用しません。|
|TDN_DIALOG_CONSTRUCTED|使用しません。|使用しません。|
|TDN_VERIFICATION_CLICKED|チェックボックスがオンの場合は1。それ以外の場合は0。|使用しません。|
|TDN_HELP|使用しません。|使用しません。|
|TDN_EXPANDO_BUTTON_CLICKED|展開領域が折りたたまれている場合は0。展開テキストが表示される場合は0以外の。|使用しません。|

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[チュートリアル: アプリケーションへの CTaskDialog の追加](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
