---
title: CUserToolsManager クラス
ms.date: 11/04/2016
f1_keywords:
- CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CreateNewTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::FindTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetArgumentsMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetFilter
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetInitialDirMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetMaxTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetToolsEntryCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetUserTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::InvokeTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::IsUserToolCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::LoadState
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolDown
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolUp
- AFXUSERTOOLSMANAGER/CUserToolsManager::RemoveTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::SaveState
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetFilter
helpviewer_keywords:
- CUserToolsManager [MFC], CUserToolsManager
- CUserToolsManager [MFC], CreateNewTool
- CUserToolsManager [MFC], FindTool
- CUserToolsManager [MFC], GetArgumentsMenuID
- CUserToolsManager [MFC], GetDefExt
- CUserToolsManager [MFC], GetFilter
- CUserToolsManager [MFC], GetInitialDirMenuID
- CUserToolsManager [MFC], GetMaxTools
- CUserToolsManager [MFC], GetToolsEntryCmd
- CUserToolsManager [MFC], GetUserTools
- CUserToolsManager [MFC], InvokeTool
- CUserToolsManager [MFC], IsUserToolCmd
- CUserToolsManager [MFC], LoadState
- CUserToolsManager [MFC], MoveToolDown
- CUserToolsManager [MFC], MoveToolUp
- CUserToolsManager [MFC], RemoveTool
- CUserToolsManager [MFC], SaveState
- CUserToolsManager [MFC], SetDefExt
- CUserToolsManager [MFC], SetFilter
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
ms.openlocfilehash: 857e86184e1b7ea399787520e9c4701547185133
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323373"
---
# <a name="cusertoolsmanager-class"></a>CUserToolsManager クラス

コレクションを保持[CUserTool クラス](../../mfc/reference/cusertool-class.md)アプリケーション内のオブジェクト。 ユーザー ツールは、外部アプリケーションを実行するメニュー項目です。 `CUserToolsManager` オブジェクトは、ユーザーまたは開発者がアプリケーションに新しいユーザー ツールを追加できるようにします。 ユーザー ツールに関連するコマンドの実行をサポートし、Windows レジストリにユーザー ツールに関する情報を保存します。

## <a name="syntax"></a>構文

```
class CUserToolsManager : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CUserToolsManager::CUserToolsManager](#cusertoolsmanager)|`CUserToolsManager` を構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CUserToolsManager::CreateNewTool](#createnewtool)|新しいユーザー ツールを作成します。|
|[CUserToolsManager::FindTool](#findtool)|ポインターを返します、`CMFCUserTool`指定したコマンド ID に関連付けられているオブジェクト|
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|関連付けられているリソース ID を返します、**引数**メニューで、**ツール**のタブ、**カスタマイズ** ダイアログ ボックス。|
|[CUserToolsManager::GetDefExt](#getdefext)|既定の拡張子を返します、**ファイルを開く** ダイアログ ボックス ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) では、**コマンド**フィールドに、**ツール**のタブ、**カスタマイズ** ダイアログ ボックス。|
|[CUserToolsManager::GetFilter](#getfilter)|ファイル フィルターを返します、**ファイルを開く** ダイアログ ボックス ( [CFileDialog クラス](../../mfc/reference/cfiledialog-class.md)) では、**コマンド**フィールドに、**ツール**のタブ、**カスタマイズ** ダイアログ ボックス。|
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|関連付けられているリソース ID を返します、**初期ディレクトリ**メニューで、**ツール**のタブ、**カスタマイズ** ダイアログ ボックス。|
|[CUserToolsManager::GetMaxTools](#getmaxtools)|アプリケーションに割り当てることができるユーザー ツールの最大数を返します。|
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|ユーザー ツールのメニュー項目のプレース ホルダーのコマンド ID を返します。|
|[CUserToolsManager::GetUserTools](#getusertools)|ユーザー ツールの一覧への参照を返します。|
|[CUserToolsManager::InvokeTool](#invoketool)|指定したコマンド ID を持つユーザー ツールに関連付けられているアプリケーションを実行します。|
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|コマンド ID がユーザー ツールを使用して関連付けられているかどうかを判断します。|
|[CUserToolsManager::LoadState](#loadstate)|Windows レジストリからユーザー ツールに関する情報を読み込みます。|
|[CUserToolsManager::MoveToolDown](#movetooldown)|ユーザー ツールの一覧で、下の指定されたユーザー ツールを移動します。|
|[CUserToolsManager::MoveToolUp](#movetoolup)|ユーザー ツールの一覧で指定したユーザー ツールに移動します。|
|[CUserToolsManager::RemoveTool](#removetool)|アプリケーションから、指定されたユーザー ツールを削除します。|
|[CUserToolsManager::SaveState](#savestate)|ユーザー ツールに関する情報を Windows レジストリに格納します。|
|[CUserToolsManager::SetDefExt](#setdefext)|既定の拡張子を指定する、**ファイルを開く** ダイアログ ボックス ( [CFileDialog クラス](../../mfc/reference/cfiledialog-class.md)) では、**コマンド**フィールドに、**ツール** タブ**カスタマイズ** ダイアログ ボックス。|
|[CUserToolsManager::SetFilter](#setfilter)|ファイル フィルターを指定します、**ファイルを開く** ダイアログ ボックス ( [CFileDialog クラス](../../mfc/reference/cfiledialog-class.md)) では、**コマンド**フィールドに、**ツール**のタブ、**カスタマイズ** ダイアログ ボックス。|

## <a name="remarks"></a>Remarks

ユーザー ツールをアプリケーションに組み込むには、次の必要があります。

1. メニュー項目とユーザー ツールのメニュー エントリに関連付けられているコマンド ID を予約します。

2. ユーザーは、アプリケーションで定義できる各ユーザー ツールの連番のコマンド ID を予約します。

3. 呼び出す、 [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)メソッドと、次のパラメーターを指定する: メニュー コマンド ID、最初のユーザー ツールのコマンド ID、およびツールのユーザーの最後のコマンド id。

必要がある 1 つだけグローバル`CUserToolsManager`アプリケーションごとのオブジェクト。

ユーザー ツールの例は、VisualStudioDemo サンプル プロジェクトを参照してください。

## <a name="example"></a>例

次の例への参照を取得する方法を示します、`CUserToolsManager`オブジェクトと、新しいユーザー ツールを作成する方法。 このコード スニペットの一部、 [Visual Studio のデモ サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CUserToolsManager`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxusertoolsmanager.h

##  <a name="createnewtool"></a>  CUserToolsManager::CreateNewTool

新しいユーザー ツールを作成します。

```
CUserTool* CreateNewTool();
```

### <a name="return-value"></a>戻り値

新しく作成したユーザーのツール、または NULL ユーザー ツールの数が最大値を超過した場合へのポインター。 返される型に渡される型と同じ`CWinAppEx::EnableUserTools`として、 *pToolRTC*パラメーター。

### <a name="remarks"></a>Remarks

このメソッドの呼び出しで指定されている範囲内の最初の使用可能なメニュー コマンド ID の検索[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)とユーザー ツールにこの ID を割り当てます。

メソッドは、多数のツールは、上限に達した場合に失敗します。 これには、範囲内のすべてのコマンド Id は、ユーザー ツールに割り当てられているときに発生します。 ツールの最大数を取得するには呼び出すことによって[CUserToolsManager::GetMaxTools](#getmaxtools)します。 ツールの一覧へのアクセスを呼び出して取得することができます、 [CUserToolsManager::GetUserTools](#getusertools)メソッド。

##  <a name="cusertoolsmanager"></a>  CUserToolsManager::CUserToolsManager

`CUserToolsManager` を構築します。 各アプリケーションは、1 つのユーザー ツール マネージャー多くてが必要です。

```
CUserToolsManager();

CUserToolsManager(
    const UINT uiCmdToolsDummy,
    const UINT uiCmdFirst,
    const UINT uiCmdLast,
    CRuntimeClass* pToolRTC=RUNTIME_CLASS(CUserTool),
    UINT uArgMenuID=0,
    UINT uInitDirMenuID=0);
```

### <a name="parameters"></a>パラメーター

*uiCmdToolsDummy*<br/>
[in]ユーザーの [ツール] メニューのコマンド ID プレース ホルダーとして、フレームワークを使用して符号なし整数。

*uiCmdFirst*<br/>
[in]最初のユーザー ツールのコマンドのコマンド ID。

*uiCmdLast*<br/>
[in]最後のユーザー ツールのコマンドのコマンド ID。

*pToolRTC*<br/>
[in]クラスを[CUserToolsManager::CreateNewTool](#createnewtool)を作成します。 派生型を使用するこのクラスを使用すると、 [CUserTool クラス](../../mfc/reference/cusertool-class.md)既定の実装ではなく。

*uArgMenuID*<br/>
[in]引数のポップアップ メニューのメニュー リソースの ID。

*uInitDirMenuID*<br/>
[in][初期ディレクトリ] のポップアップ メニューのメニュー リソースの ID。

### <a name="remarks"></a>Remarks

このコンス トラクターを呼び出さないでください。 代わりに、 [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)を有効にするユーザーのツール、および呼び出し[CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager)へのポインターを取得する、`CUserToolsManager`します。 詳細については、次を参照してください。[ユーザー定義のツール](../../mfc/user-defined-tools.md)します。

##  <a name="findtool"></a>  CUserToolsManager::FindTool

ポインターを返します、 [CUserTool クラス](../../mfc/reference/cusertool-class.md)指定したコマンド ID に関連付けられているオブジェクト

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>パラメーター

*uiCmdId*<br/>
[in]メニュー コマンドの識別子。

### <a name="return-value"></a>戻り値

ポインターを[CUserTool クラス](../../mfc/reference/cusertool-class.md)または`CUserTool`-派生オブジェクトの場合は成功した場合。 それ以外の場合 NULL です。

### <a name="remarks"></a>Remarks

ときに`FindTool`が成功すると、返される型は、の型と同じ、 *pToolRTC*パラメーターを[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)します。

##  <a name="getargumentsmenuid"></a>  CUserToolsManager::GetArgumentsMenuID

関連付けられているリソース ID を返します、**引数**メニューで、**ツール**のタブ、**カスタマイズ** ダイアログ ボックス。

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>戻り値

メニュー リソースの識別子。

### <a name="remarks"></a>Remarks

*UArgMenuID*パラメーターの[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)リソースの ID を指定します。

##  <a name="getdefext"></a>  CUserToolsManager::GetDefExt

既定の拡張子を返します、**ファイルを開く** ダイアログ ボックス ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) では、**コマンド**フィールドに、**ツール**のタブ、**カスタマイズ** ダイアログ ボックス。

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>戻り値

参照、`CString`拡張子を表すオブジェクト。

##  <a name="getfilter"></a>  CUserToolsManager::GetFilter

ファイル フィルターを返します、**ファイルを開く** ダイアログ ボックス ( [CFileDialog クラス](../../mfc/reference/cfiledialog-class.md)) では、**コマンド**フィールドに、**ツール**のタブ、**カスタマイズ** ダイアログ ボックス。

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>戻り値

参照、`CString`フィルターを格納しているオブジェクト。

##  <a name="getinitialdirmenuid"></a>  CUserToolsManager::GetInitialDirMenuID

関連付けられているリソース ID を返します、**初期ディレクトリ**メニューで、**ツール**のタブ、**カスタマイズ** ダイアログ ボックス。

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>戻り値

メニュー リソースの識別子です。

### <a name="remarks"></a>Remarks

返された ID が指定された、 *uInitDirMenuID*パラメーターの[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)します。

##  <a name="getmaxtools"></a>  CUserToolsManager::GetMaxTools

アプリケーションに割り当てることができるユーザー ツールの最大数を返します。

```
int GetMaxTools() const;
```

### <a name="return-value"></a>戻り値

割り当てることができるユーザー ツールの最大数。

### <a name="remarks"></a>Remarks

アプリケーションに割り当てることができるツールの最大数を取得するには、このメソッドを呼び出します。 この数値が範囲内で Id の数、 *uiCmdFirst*を通じて、 *uiCmdLast*に渡すパラメーター [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。

##  <a name="gettoolsentrycmd"></a>  CUserToolsManager::GetToolsEntryCmd

ユーザー ツールのメニュー項目のプレース ホルダーのコマンド ID を返します。

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>戻り値

プレース ホルダーのコマンド ID。

### <a name="remarks"></a>Remarks

ユーザー ツールを有効にするには呼び出します[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)します。 *UiCmdToolsDummy*パラメーター ツール エントリ コマンドのコマンド ID を指定します。 このメソッドは、ツールのエントリのコマンド ID を返します。 メニューでその ID を使用する任意の場所は、メニューが表示されるユーザー ツールの一覧に置換されます。

##  <a name="getusertools"></a>  CUserToolsManager::GetUserTools

ユーザー ツールの一覧への参照を返します。

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>戻り値

Const 参照を[CObList クラス](../../mfc/reference/coblist-class.md)ユーザー ツールの一覧を格納しているオブジェクト。

### <a name="remarks"></a>Remarks

ツールのユーザーの一覧を取得するには、このメソッドを呼び出し、 [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)オブジェクトを保持します。 各ユーザー ツールは、型のオブジェクトで表される[CUserTool クラス](../../mfc/reference/cusertool-class.md)から派生した型または`CUserTool`します。 型がで指定された、 *pToolRTC*パラメーターを呼び出すと[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)ユーザー ツールを有効にします。

##  <a name="invoketool"></a>  CUserToolsManager::InvokeTool

指定したコマンド ID を持つユーザー ツールに関連付けられているアプリケーションを実行します。

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>パラメーター

*uiCmdId*<br/>
[in]ユーザー ツールに関連付けられているメニュー コマンド ID。

### <a name="return-value"></a>戻り値

ユーザー ツールに関連付けられたコマンドが正常に実行された場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

ツールのユーザーに関連付けられているアプリケーションを実行するには、このメソッドの呼び出しがで指定されたコマンド ID を持つ*uiCmdId*します。

##  <a name="isusertoolcmd"></a>  CUserToolsManager::IsUserToolCmd

コマンド ID がユーザー ツールを使用して関連付けられているかどうかを判断します。

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>パラメーター

*uiCmdId*<br/>
[in]メニュー項目のコマンド ID。

### <a name="return-value"></a>戻り値

指定したコマンド ID がユーザー ツール; に関連付けられている場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

このメソッドは、指定したコマンド ID がコマンド ID の範囲内かどうかを確認します。 呼び出すときに範囲を指定する[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)ユーザー ツールを有効にします。

##  <a name="loadstate"></a>  CUserToolsManager::LoadState

Windows レジストリからユーザー ツールに関する情報を読み込みます。

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
[in]Windows のレジストリ キーのパス。

### <a name="return-value"></a>戻り値

状態が正常に読み込まれている場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

このメソッドの状態を読み込みます、 `CUserToolsManager` Windows レジストリからのオブジェクト。

通常、このメソッドを直接呼び出すことはできません。 [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate)はワークスペースの初期化プロセスの一環として関数を呼び出します。

##  <a name="movetooldown"></a>  CUserToolsManager::MoveToolDown

ユーザー ツールの一覧で、下の指定されたユーザー ツールを移動します。

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>パラメーター

*pTool*<br/>
[in]移動するユーザー ツールを指定します。

### <a name="return-value"></a>戻り値

ユーザー ツールが正常に下へ移動された場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

メソッドは失敗、ツールを*pTool*を指定します内部リストにない場合、またはツールが、一覧の最後にします。

##  <a name="movetoolup"></a>  CUserToolsManager::MoveToolUp

ユーザー ツールの一覧で指定したユーザー ツールに移動します。

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>パラメーター

*pTool*<br/>
[in]移動するユーザー ツールを指定します。

### <a name="return-value"></a>戻り値

ユーザー ツール正常に移動された場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

メソッドは失敗ツールを*pTool*パラメーターは、内部リストにないを指定しますまたは、このツールは、一覧の最初のツール項目。

##  <a name="removetool"></a>  CUserToolsManager::RemoveTool

アプリケーションから、指定されたユーザー ツールを削除します。

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>パラメーター

*pTool*<br/>
[入力、出力]削除するユーザー ツールへのポインター。

### <a name="return-value"></a>戻り値

TRUE の場合、ツールが正常に削除されました。 それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドは、削除、ツールが正常に削除されると場合、 *pTool*します。

##  <a name="savestate"></a>  CUserToolsManager::SaveState

ユーザー ツールに関する情報を Windows レジストリに格納します。

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
[in]Windows レジストリ キーへのパス。

### <a name="return-value"></a>戻り値

状態が正常に保存されている場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

メソッドの現在の状態を格納する、 `CUserToolsManager` Windows レジストリ内のオブジェクト。

このメソッドを直接呼び出すにする必要はありません[CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)アプリケーションのワークスペースのシリアル化プロセスの一部として自動的にそれを呼び出します。

##  <a name="setdefext"></a>  CUserToolsManager::SetDefExt

既定の拡張子を指定する、**ファイルを開く** ダイアログ ボックス ( [CFileDialog クラス](../../mfc/reference/cfiledialog-class.md)) では、**コマンド**フィールドに、**ツール** タブ**カスタマイズ** ダイアログ ボックス。

```
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>パラメーター

*strDefExt*<br/>
[in]既定のファイル名拡張子を含むテキスト文字列。

### <a name="remarks"></a>Remarks

既定のファイル名拡張子を指定するには、このメソッドを呼び出す、**ファイルを開く**ダイアログ ボックスで、ユーザーが ユーザー ツールに関連付けるアプリケーションが表示されます。 既定では"exe です"。

##  <a name="setfilter"></a>  CUserToolsManager::SetFilter

ファイル フィルターを指定します、**ファイルを開く** ダイアログ ボックス ( [CFileDialog クラス](../../mfc/reference/cfiledialog-class.md)) では、**コマンド**フィールドに、**ツール**のタブ、**カスタマイズ** ダイアログ ボックス。

```
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>パラメーター

*strFilter*<br/>
[in]フィルターを指定します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx クラス](../../mfc/reference/cwinappex-class.md)<br/>
[CUserTool クラス](../../mfc/reference/cusertool-class.md)
