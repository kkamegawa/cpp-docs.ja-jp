---
title: CUserTool クラス
ms.date: 11/04/2016
f1_keywords:
- CUserTool
- AFXUSERTOOL/CUserTool
- AFXUSERTOOL/CUserTool::CopyIconToClipboard
- AFXUSERTOOL/CUserTool::DrawToolIcon
- AFXUSERTOOL/CUserTool::GetCommand
- AFXUSERTOOL/CUserTool::GetCommandId
- AFXUSERTOOL/CUserTool::Invoke
- AFXUSERTOOL/CUserTool::Serialize
- AFXUSERTOOL/CUserTool::SetCommand
- AFXUSERTOOL/CUserTool::SetToolIcon
- AFXUSERTOOL/CUserTool::LoadDefaultIcon
- AFXUSERTOOL/CUserTool::m_strArguments
- AFXUSERTOOL/CUserTool::m_strInitialDirectory
- AFXUSERTOOL/CUserTool::m_strLabel
helpviewer_keywords:
- CUserTool [MFC], CopyIconToClipboard
- CUserTool [MFC], DrawToolIcon
- CUserTool [MFC], GetCommand
- CUserTool [MFC], GetCommandId
- CUserTool [MFC], Invoke
- CUserTool [MFC], Serialize
- CUserTool [MFC], SetCommand
- CUserTool [MFC], SetToolIcon
- CUserTool [MFC], LoadDefaultIcon
- CUserTool [MFC], m_strArguments
- CUserTool [MFC], m_strInitialDirectory
- CUserTool [MFC], m_strLabel
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
ms.openlocfilehash: b73cb3d3c6e244a9aa41a91a3ee9ff1efa98d496
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502241"
---
# <a name="cusertool-class"></a>CUserTool クラス

ユーザー ツールは、外部アプリケーションを実行するメニュー項目です。 ユーザーは、 **[カスタマイズ]** ダイアログボックス ( [Cmfctoolbarscustomizedialog クラス](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) の **[ツール]** タブを使用して、ユーザーツールを追加したり、各ユーザーツールの名前、コマンド、引数、および初期ディレクトリを指定したりすることができます。

## <a name="syntax"></a>構文

```
class CUserTool : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CUserTool:: CopyIconToClipboard](#copyicontoclipboard)||
|[CUserTool::D rawToolIcon](#drawtoolicon)|指定した四角形にユーザーツールアイコンを描画します。|
|[CUserTool::GetCommand](#getcommand)|ユーザーツールに関連付けられているコマンドのテキストを含む文字列を返します。|
|[CUserTool::GetCommandId](#getcommandid)|ユーザーツールのメニュー項目のコマンド ID を返します。|
|[CUserTool::Invoke](#invoke)|ユーザーツールに関連付けられたコマンドを実行します。|
|[CUserTool:: Serialize](#serialize)|アーカイブに対して、このオブジェクトの読み取りまたは書き込みを行います。 ( [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)をオーバーライドします)。|
|[CUserTool::SetCommand](#setcommand)|ユーザーツールに関連付けられたコマンドを設定します。|
|[CUserTool::SetToolIcon](#settoolicon)|ツールに関連付けられているアプリケーションからユーザーツールのアイコンを読み込みます。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|ユーザーツールの既定のアイコンを読み込みます。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CUserTool:: m_strArguments](#m_strarguments)|ユーザーツールのコマンドライン引数。|
|[CUserTool:: m_strInitialDirectory](#m_strinitialdirectory)|ユーザーツールの初期ディレクトリ。|
|[CUserTool:: m_strLabel](#m_strlabel)|ツールのメニュー項目に表示されるツール名。|

## <a name="remarks"></a>Remarks

アプリケーションでユーザーツールを有効にする方法の詳細については、「 [Cusertools Manager クラス](../../mfc/reference/cusertoolsmanager-class.md)」を参照してください。

## <a name="example"></a>例

次の例は、 `CUserToolsManager`オブジェクトからツールを作成し、 `m_strLabel`メンバー変数を設定し、ユーザーツールが実行するアプリケーションを設定する方法を示しています。 このコードスニペットは、 [Visual Studio のデモサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxusertool

##  <a name="copyicontoclipboard"></a>  CUserTool::CopyIconToClipboard

詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="drawtoolicon"></a>CUserTool::D rawToolIcon

指定した四角形の中央にユーザーツールアイコンを描画します。

```
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からデバイスコンテキストへのポインター。

*rectImage*<br/>
からアイコンを表示する領域の座標を指定します。

##  <a name="getcommand"></a>  CUserTool::GetCommand

ユーザーツールに関連付けられているコマンドのテキストを含む文字列を返します。

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>戻り値

ユーザーツールに`CString`関連付けられているコマンドのテキストを格納しているオブジェクトへの参照。

##  <a name="getcommandid"></a>  CUserTool::GetCommandId

ユーザーツールのコマンド ID を返します。

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>戻り値

このユーザーツールのコマンド ID。

##  <a name="invoke"></a>  CUserTool::Invoke

ユーザーツールに関連付けられたコマンドを実行します。

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>戻り値

コマンドが正常に実行された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

ユーザーツールに関連付けられているコマンドを実行するために、 [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew)を呼び出します。 コマンドが空の場合、または[ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew)が失敗した場合、関数は失敗します。

##  <a name="loaddefaulticon"></a>  CUserTool::LoadDefaultIcon

ユーザーツールの既定のアイコンを読み込みます。

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>戻り値

読み込まれたアイコン (HICON) を示すハンドル。既定のアイコンを読み込むことができない場合は NULL。

### <a name="remarks"></a>Remarks

フレームワークは、ツールの実行可能ファイルからユーザー定義ツールのアイコンを読み込むことができない場合に、このメソッドを呼び出します。

このメソッドをオーバーライドして、独自の既定のツールアイコンを指定します。

##  <a name="m_strarguments"></a>CUserTool:: m_strArguments

ユーザーツールのコマンドライン引数。

```
CString m_strArguments;
```

### <a name="remarks"></a>Remarks

この文字列は、 [Cusertool:: Invoke](#invoke)を呼び出したとき、またはユーザーがこのツールに関連付けられたコマンドをクリックしたときに、ツールに渡されます。

##  <a name="m_strinitialdirectory"></a>CUserTool:: m_strInitialDirectory

ユーザーツールの初期ディレクトリを指定します。

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>Remarks

この変数は、 [Cusertool:: Invoke](#invoke)を呼び出すとき、またはユーザーがこのツールに関連付けられたコマンドをクリックしたときに、ツールによって実行される初期ディレクトリを指定します。

##  <a name="m_strlabel"></a>CUserTool:: m_strLabel

ツールのメニュー項目に表示されるラベル。

```
CString m_strLabel;
```

##  <a name="serialize"></a>  CUserTool::Serialize

詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>パラメーター

から*ar*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setcommand"></a>  CUserTool::SetCommand

ユーザーツールが実行するアプリケーションを設定します。

```
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>パラメーター

*lpszCmd*<br/>
からユーザーツールに関連付けられる新しいアプリケーションを指定します。

### <a name="remarks"></a>Remarks

ユーザーツールが実行する新しいアプリケーションを設定するには、このメソッドを呼び出します。 メソッドは、古いアイコンを破棄し、指定されたアプリケーションから新しいアイコンを読み込みます。 アプリケーションからアイコンを読み込むことができない場合は、 [Cusertool:: LoadDefaultIcon](#loaddefaulticon)を呼び出すことによって、ユーザーツールの既定のアイコンが読み込まれます。

##  <a name="settoolicon"></a>  CUserTool::SetToolIcon

ツールが使用するアプリケーションからユーザーツールのアイコンを読み込みます。

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>戻り値

読み込まれたアイコンへのハンドル。

### <a name="remarks"></a>Remarks

メニュー項目に表示されるアイコンを読み込むには、このメソッドを呼び出します。 このメソッドは、ツールが使用する実行可能ファイル内のアイコンを検索します。 既定のアイコンがない場合は、 [Cusertool:: LoadDefaultIcon](#loaddefaulticon)によって提供されるアイコンが代わりに使用されます。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx クラス](../../mfc/reference/cwinappex-class.md)<br/>
[CUserToolsManager クラス](../../mfc/reference/cusertoolsmanager-class.md)
