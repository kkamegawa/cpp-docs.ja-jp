---
title: Cのマネージャークラス
ms.date: 11/04/2016
f1_keywords:
- CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CleanUp
- AFXKEYBOARDMANAGER/CKeyboardManager::FindDefaultAccelerator
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyHandled
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyPrintable
- AFXKEYBOARDMANAGER/CKeyboardManager::IsShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::LoadState
- AFXKEYBOARDMANAGER/CKeyboardManager::ResetAll
- AFXKEYBOARDMANAGER/CKeyboardManager::SaveState
- AFXKEYBOARDMANAGER/CKeyboardManager::ShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::TranslateCharToUpper
- AFXKEYBOARDMANAGER/CKeyboardManager::UpdateAccelTable
helpviewer_keywords:
- CKeyboardManager [MFC], CKeyboardManager
- CKeyboardManager [MFC], CleanUp
- CKeyboardManager [MFC], FindDefaultAccelerator
- CKeyboardManager [MFC], IsKeyHandled
- CKeyboardManager [MFC], IsKeyPrintable
- CKeyboardManager [MFC], IsShowAllAccelerators
- CKeyboardManager [MFC], LoadState
- CKeyboardManager [MFC], ResetAll
- CKeyboardManager [MFC], SaveState
- CKeyboardManager [MFC], ShowAllAccelerators
- CKeyboardManager [MFC], TranslateCharToUpper
- CKeyboardManager [MFC], UpdateAccelTable
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
ms.openlocfilehash: e4f8f678e76113b5d012242f474ff0ab8b0628dd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505777"
---
# <a name="ckeyboardmanager-class"></a>Cのマネージャークラス

メイン フレーム ウィンドウおよび子フレーム ウィンドウのショートカット キーのテーブルを管理します。

## <a name="syntax"></a>構文

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|||
|-|-|
|名前|説明|
|[C# manager:: Cのマネージャー](#ckeyboardmanager)|`CKeyboardManager` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|名前|説明|
|[C、Manager:: CleanUp](#cleanup)|ショートカットキーのテーブルを消去します。|
|[C/Manager:: FindDefaultAccelerator](#finddefaultaccelerator)|指定したコマンドおよびウィンドウの既定のショートカットキーを取得します。|
|[C、Manager:: IsKeyHandled](#iskeyhandled)|キーがアクセラレータテーブルによって処理されるかどうかを判断します。|
|[CIsKeyPrintable Manager::](#iskeyprintable)|文字が印刷可能かどうかを示します。|
|[CIsShowAllAccelerators Manager::](#isshowallaccelerators)|メニューがコマンドのすべてのショートカットキーを表示するか、既定のショートカットキーのみを表示するかを示します。|
|[CLoadState Manager::](#loadstate)|Windows レジストリからショートカットキーのテーブルを読み込みます。|
|[C、Manager:: ResetAll](#resetall)|アプリケーションリソースからショートカットキーテーブルを再読み込みします。|
|[CSaveState Manager::](#savestate)|ショートカットキーテーブルを Windows レジストリに保存します。|
|[CShowAllAccelerators Manager::](#showallaccelerators)|フレームワークですべてのコマンドのすべてのショートカットキーを表示するか、各コマンドの単一のショートカットキーを表示するかを指定します。 このメソッドは、関連付けられたショートカットキーを1つだけ持つコマンドには影響しません。|
|[CTranslateCharToUpper Manager::](#translatechartoupper)|文字を上位レジスタに変換します。|
|[CUpdateAccelTable Manager::](#updateacceltable)|ショートカットキーテーブルを新しいショートカットキーテーブルで更新します。|

## <a name="remarks"></a>Remarks

このクラスのメンバーを使用すると、Windows レジストリにショートカットキーテーブルを保存して読み込むことができ、テンプレートを使用してショートカットキーテーブルを更新し、フレームウィンドウ内のコマンドの既定のショートカットキーを見つけることができます。 また`CKeyboardManager` 、オブジェクトを使用すると、ユーザーにショートカットキーを表示する方法を制御できます。

オブジェクトを`CKeyboardManager`手動で作成しないでください。 アプリケーションのフレームワークによって自動的に作成されます。 ただし、アプリケーションの初期化プロセスでは、 [CWinAppEx:: Init manager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)を呼び出す必要があります。 アプリケーションのキーボードマネージャーへのポインターを取得するには、 [CWinAppEx:: Getkeyboard manager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)を呼び出します。

## <a name="example"></a>例

次の例は、 `CKeyboardManager` `CWinAppEx`クラスからオブジェクトへのポインターを取得する方法と、メニューコマンドに関連付けられているすべてのショートカットキーを表示する方法を示しています。 このコードスニペットは、[カスタムページサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxkeyboardmanager

##  <a name="ckeyboardmanager"></a>C# manager:: Cのマネージャー

`CKeyboardManager` オブジェクトを構築します。

```
CKeyboardManager();
```

### <a name="remarks"></a>Remarks

ほとんどの場合、を`CKeyboardManager`直接作成する必要はありません。 既定では、フレームワークによって作成されます。 への`CKeyboardManager`ポインターを取得するには、 [CWinAppEx:: 表示 manager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)を呼び出します。 手動で作成する場合は、メソッド[CWinAppEx:: Init、manager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)を使用して初期化する必要があります。

##  <a name="cleanup"></a>C、Manager:: CleanUp

リソースを`CKeyboardManager`解放し、すべてのショートカットキーマッピングをクリアします。

```
static void CleanUp();
```

### <a name="remarks"></a>Remarks

ショートカットキーの詳細については、「[キーボードおよびマウスのカスタマイズ](../../mfc/keyboard-and-mouse-customization.md)」を参照してください。

アプリケーションの終了時にフレームワークによって自動的に呼び出されるため、アプリケーションの終了時にこの関数を呼び出す必要はありません。

##  <a name="finddefaultaccelerator"></a>C/Manager:: FindDefaultAccelerator

指定したコマンドおよびウィンドウの既定のショートカットキーを取得します。

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
からコマンド ID。

*str*<br/>
入出力`CString`オブジェクトへの参照。

*pWndFrame*<br/>
からフレームウィンドウへのポインター。

*bIsDefaultFrame*<br/>
からフレームウィンドウが既定のフレームウィンドウであるかどうかを指定します。

### <a name="return-value"></a>戻り値

ショートカットが見つかった場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このメソッドは、 *uiCmd*によって指定されたコマンドを検索し、既定のショートカットキーを取得します。 次に、このショートカットキーに関連付けられている文字列を取得し、その値を*str*パラメーターに書き込みます。

##  <a name="iskeyhandled"></a>C、Manager:: IsKeyHandled

指定されたキーが[Cのマネージャークラス](../../mfc/reference/ckeyboardmanager-class.md)によって処理されるかどうかを判断します。

```
static BOOL __stdcall IsKeyHandled(
    WORD nKey,
    BYTE fVirt,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*nKey*|から確認するキー。|
|*fVirt*|からショートカットキーの動作を指定します。 使用可能な値の一覧については、「 [ACCEL Structure](/windows/win32/api/winuser/ns-winuser-accel)」を参照してください。|
|*pWndFrame*|からフレームウィンドウ。 このメソッドは、ショートカットキーをこのフレームで処理するかどうかを決定します。|
|*bIsDefaultFrame*|から*PWndFrame*が既定のフレームウィンドウであるかどうかを示すブール型パラメーターです。|

### <a name="return-value"></a>戻り値

ショートカットキーが処理される場合は TRUE。 キーが処理されない場合、または*pWndFrame*が NULL の場合は FALSE。

### <a name="remarks"></a>Remarks

入力パラメーターは、 *pWndFrame*でショートカットキーが処理されるかどうかを判断*するために*、アクセスキーと*fVirt*の両方のアクセラレータテーブルのエントリと一致する必要があります。

##  <a name="iskeyprintable"></a>CIsKeyPrintable Manager::

文字が印刷可能かどうかを示します。

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*nChar*|からこのメソッドがチェックする文字。|

### <a name="return-value"></a>戻り値

文字が印刷可能な場合は0以外の値。それ以外の場合は0。

### <a name="remarks"></a>Remarks

[Getの](/windows/win32/api/winuser/nf-winuser-getkeyboardstate)呼び出しが失敗した場合、このメソッドは失敗します。

##  <a name="isshowallaccelerators"></a>CIsShowAllAccelerators Manager::

メニューコマンドに関連付けられているすべてのショートカットキーまたは既定のショートカットキーのみをメニューに表示するかどうかを示します。

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>戻り値

アプリケーションがメニューコマンドのすべてのショートカットキーを一覧表示する場合は0以外の。アプリケーションが既定のショートカットキーのみを表示する場合は0。

### <a name="remarks"></a>Remarks

アプリケーションには、メニューバーのメニューコマンドのショートカットキーが一覧表示されます。 関数[ckeys manager:: ShowAllAccelerators](#showallaccelerators)を使用して、アプリケーションがすべてのショートカットキーを一覧表示するか、既定のショートカットキーだけを表示するかを制御します。

##  <a name="loadstate"></a>CLoadState Manager::

Windows レジストリからショートカットキーのテーブルを読み込みます。

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
からデータが保存さ`CKeyboardManager`れるレジストリパス。

*pDefaultFrame*<br/>
から既定のウィンドウとして使用するフレームウィンドウへのポインター。

### <a name="return-value"></a>戻り値

状態が正常に読み込まれた場合は0以外の場合は。それ以外の場合は0。

### <a name="remarks"></a>Remarks

*Lpszprofilename*パラメーターが NULL の場合、このメソッドは、データの`CKeyboardManager`既定のレジストリの場所を確認します。 既定のレジストリの場所は、 [CWinAppEx クラス](../../mfc/reference/cwinappex-class.md)によって指定されます。 データは、前に[CSaveState manager::](#savestate)メソッドを使用して書き込む必要があります。

既定のウィンドウを指定しない場合は、アプリケーションのメインフレームウィンドウが使用されます。

##  <a name="resetall"></a>C、Manager:: ResetAll

アプリケーションリソースからショートカットキーテーブルを再読み込みします。

```
void ResetAll();
```

### <a name="remarks"></a>Remarks

この関数は、 `CKeyboardManager`インスタンスに格納されているショートカットをクリアします。 その後、アプリケーションリソースからキーボードマネージャーの状態が再度読み込まれます。

##  <a name="savestate"></a>CSaveState Manager::

ショートカットキーテーブルを Windows レジストリに保存します。

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
から状態を`CKeyboardManager`保存するためのレジストリパス。

*pDefaultFrame*<br/>
から既定のウィンドウになるフレームウィンドウへのポインター。

### <a name="return-value"></a>戻り値

キーボードマネージャーの状態が正常に保存された場合は0以外。それ以外の場合は0。

### <a name="remarks"></a>Remarks

*Lpszprofilename*パラメーターが NULL の場合、このメソッドは、 `CKeyboardManager` [CWinAppEx クラス](../../mfc/reference/cwinappex-class.md)によって指定された既定の場所に状態を書き込みます。 場所を指定する場合は、後で[CLoadState manager::](#loadstate)メソッドを使用してデータを読み込むことができます。

既定のウィンドウを指定しない場合は、メインフレームウィンドウが既定のウィンドウとして使用されます。

##  <a name="showallaccelerators"></a>CShowAllAccelerators Manager::

メニューコマンドに関連付けられているすべてのショートカットキーを表示します。

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>パラメーター

*bShowAll*<br/>
からTRUE の場合、すべてのショートカットキーが表示されます。 FALSE の場合は、最初のショートカットキーのみが表示されます。

*lpszDelimiter*<br/>
からショートカットキーの間に挿入する文字列。 ショートカットキーが1つだけ表示されている場合、この区切り記号は効果がありません。

### <a name="remarks"></a>Remarks

既定では、コマンドに複数のショートカットキーが関連付けられている場合、最初のショートカットキーのみが表示されます。 この関数を使用すると、すべてのコマンドに関連付けられているすべてのショートカットキーを一覧表示できます。

ショートカットキーは、メニューバーのコマンドの横に一覧表示されます。 すべてのショートカットキーが表示されている場合は、 *Lpszdelimiter*によって指定された文字列によって、個々のショートカットキーが分離されます。

##  <a name="translatechartoupper"></a>CTranslateCharToUpper Manager::

文字を上位レジスタに変換します。

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>パラメーター

*nChar*<br/>
から変換する文字。

### <a name="return-value"></a>戻り値

入力パラメーターの上位レジスタである文字。

##  <a name="updateacceltable"></a>CUpdateAccelTable Manager::

ショートカットキーテーブルを新しいショートカットキーテーブルで更新します。

```
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    LPACCEL lpAccel,
    int nSize,
    CFrameWnd* pDefaultFrame = NULL);

BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    HACCEL hAccelNew,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>パラメーター

*pTemplate*<br/>
からドキュメントテンプレートへのポインター。

*lpAccel*<br/>
から新しいショートカットキーへのポインター。

*nSize*<br/>
から新しいショートカットテーブルのサイズ。

*pDefaultFrame*<br/>
から既定のフレームウィンドウへのポインター。

*hAccelNew*<br/>
から新しいショートカットテーブルへのハンドル。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

この関数を使用すると、既存のショートカットテーブルを複数のフレームウィンドウオブジェクトの新しいショートカットキーに置き換えることができます。 関数は、ドキュメントテンプレートをパラメーターとして受け取り、指定されたドキュメントテンプレートに接続されているすべてのフレームウィンドウオブジェクトへのアクセスを取得します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx クラス](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx:: Init# manager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[キーボードとマウスのカスタマイズ](../../mfc/keyboard-and-mouse-customization.md)
