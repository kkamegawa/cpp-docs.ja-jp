---
title: CDataRecoveryHandler クラス
ms.date: 03/27/2019
f1_keywords:
- CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveAllDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::CreateDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAllAutosavedFiles
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAutosavedFile
- AFXDATARECOVERY/CDataRecoveryHandler::GenerateAutosaveFileName
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::GetDocumentListName
- AFXDATARECOVERY/CDataRecoveryHandler::GetNormalDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRecoveredDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::GetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::GetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::Initialize
- AFXDATARECOVERY/CDataRecoveryHandler::QueryRestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::ReadOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::RemoveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::ReopenPreviousDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::RestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::SaveOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::SetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::SetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::UpdateDocumentInfo
helpviewer_keywords:
- CDataRecoveryHandler [MFC], CDataRecoveryHandler
- CDataRecoveryHandler [MFC], AutosaveAllDocumentInfo
- CDataRecoveryHandler [MFC], AutosaveDocumentInfo
- CDataRecoveryHandler [MFC], CreateDocumentInfo
- CDataRecoveryHandler [MFC], DeleteAllAutosavedFiles
- CDataRecoveryHandler [MFC], DeleteAutosavedFile
- CDataRecoveryHandler [MFC], GenerateAutosaveFileName
- CDataRecoveryHandler [MFC], GetAutosaveInterval
- CDataRecoveryHandler [MFC], GetAutosavePath
- CDataRecoveryHandler [MFC], GetDocumentListName
- CDataRecoveryHandler [MFC], GetNormalDocumentTitle
- CDataRecoveryHandler [MFC], GetRecoveredDocumentTitle
- CDataRecoveryHandler [MFC], GetRestartIdentifier
- CDataRecoveryHandler [MFC], GetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], GetShutdownByRestartManager
- CDataRecoveryHandler [MFC], Initialize
- CDataRecoveryHandler [MFC], QueryRestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], ReadOpenDocumentList
- CDataRecoveryHandler [MFC], RemoveDocumentInfo
- CDataRecoveryHandler [MFC], ReopenPreviousDocuments
- CDataRecoveryHandler [MFC], RestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], SaveOpenDocumentList
- CDataRecoveryHandler [MFC], SetAutosaveInterval
- CDataRecoveryHandler [MFC], SetAutosavePath
- CDataRecoveryHandler [MFC], SetRestartIdentifier
- CDataRecoveryHandler [MFC], SetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], SetShutdownByRestartManager
- CDataRecoveryHandler [MFC], UpdateDocumentInfo
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
ms.openlocfilehash: 5c5836a11dbf9e05db5b56e0bc5c062dd1617b2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253583"
---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler クラス

`CDataRecoveryHandler`自動保存を文書化し、アプリケーションが予期せず終了した場合に復元します。

## <a name="syntax"></a>構文

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[CDataRecoveryHandler::CDataRecoveryHandler](#cdatarecoveryhandler)|`CDataRecoveryHandler` オブジェクトを構築します。|

### <a name="methods"></a>メソッド

|||
|-|-|
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|登録されている各ファイルの自動保存、`CDataRecoveryHandler`クラス。|
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|指定されたドキュメントの自動保存します。|
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|開いているドキュメントの一覧にドキュメントを追加します。|
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|現在の自動保存されたファイルをすべて削除します。|
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|指定された自動保存ファイルを削除します。|
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|指定されたドキュメントのファイル名に関連付けられている自動保存ファイルの名前を生成します。|
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|自動保存の試行間隔を返します。|
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|自動保存されたファイルのパスを返します。|
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|ドキュメントの名前を取得、`CDocument`オブジェクト。|
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|指定した文書の通常のタイトルを取得します。|
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|作成し、復元された文書のタイトルを返します。|
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|アプリケーションの再起動の一意の識別子を取得します。|
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|示すかどうか、`CDataRecoveryHandler`現在アイドル ループに対して自動保存を実行します。|
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|再起動マネージャーのアプリケーションを終了する原因となったかどうかを示します。|
|[CDataRecoveryHandler::Initialize](#initialize)|`CDataRecoveryHandler` を初期化します。|
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|各ドキュメントをユーザーにダイアログ ボックスを表示、`CDataRecoveryHandler`自動保存されます。 ダイアログ ボックスでは、ユーザーが自動保存されたドキュメントを復元するかどうかを判断します。|
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|レジストリから開いているドキュメントの一覧を読み込みます。|
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|開いているドキュメントの一覧から、指定されたドキュメントを削除します。|
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|以前に開かれているドキュメントを開きます。|
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|ユーザー入力に基づいて、自動保存されたドキュメントを復元します。|
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|現在開いているドキュメントの一覧を Windows レジストリに保存します。|
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|ミリ秒単位での自動保存のサイクルの間の時間を設定します。|
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|自動保存されたファイルが格納されるディレクトリを設定します。|
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|このインスタンスの再起動の一意の識別子を設定、`CDataRecoveryHandler`します。|
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|セットかどうか、`CDataRecoveryHandler`アイドル状態の現在のサイクル中に、開いているドキュメントの情報を Windows レジストリに保存します。|
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|再起動マネージャーによって、アプリケーションの以前の終了が発生したかどうかを設定します。|
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|そのユーザーが保存されるため、ドキュメントの情報を更新します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|m_bRestoringPreviousOpenDocs|データ回復のハンドラーが既に開いているドキュメントを再度開くかどうかを示します。|
|m_bSaveDocumentInfoOnIdle|次のアイドル ループでデータ回復のハンドラーの自動保存がドキュメントかどうかを示します。|
|m_bShutdownByRestartManager|再起動マネージャー アプリケーションを終了するかどうかを示します。|
|m_dwRestartManagerSupportFlags|アプリケーションの再起動マネージャーがサポートされる内容を示すフラグを提供します。|
|m_lstAutosavesToDelete|元のドキュメントを閉じたときに削除されなかった自動保存されたファイルの一覧。 アプリケーションの終了時、再起動マネージャーの再試行がファイルを削除します。|
|m_mapDocNameToAutosaveName|ドキュメント名と自動保存されたファイル名のマップです。|
|m_mapDocNameToDocumentPtr|ドキュメント名のマップ、 [CDocument](../../mfc/reference/cdocument-class.md)ポインター。|
|m_mapDocNameToRestoreBool|ドキュメント名と自動保存されたドキュメントを復元するかどうかを示すブール値パラメーターのマップです。|
|m_mapDocumentPtrToDocName|マップ、`CDocument`ドキュメント名へのポインター。|
|m_mapDocumentPtrToDocTitle|マップ、`CDocument`ドキュメント タイトルへのポインター。 これらのタイトルは、ファイルを保存するために使用されます。|
|m_nAutosaveInterval|自動保存の間隔をミリ秒で時間です。|
|m_nTimerID|自動保存タイマーの識別子。|
|m_strAutosavePath|自動保存されたドキュメントの保存場所。|
|m_strRestartIdentifier|再起動マネージャーの GUID の文字列形式。|

## <a name="remarks"></a>Remarks

再起動マネージャーを使用して、`CDataRecoveryHandler`保持するクラスのすべての開いているドキュメントと自動保存として追跡必要です。 自動保存を有効にするには使用、 [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)メソッド。 このメソッドは、 `CDataRecoveryHandler` next アイドル ループに対して自動保存を実行します。 再起動マネージャーの呼び出し`SetSaveDocumentInfoOnIdle`ときに、`CDataRecoveryHandler`自動保存を実行する必要があります。

すべてのメソッドの`CDataRecoveryHandler`クラスは仮想です。 独自のカスタム データ復旧のハンドラーを作成するには、このクラスのメソッドをオーバーライドします。 独自のデータ復旧ハンドラーを作成するか、マネージャーを再起動すると、しない限りを CDataRecoveryHandler がインスタンス化できません。 [CWinApp クラス](../../mfc/reference/cwinapp-class.md)作成、`CDataRecoveryHandler`オブジェクトが必要です。

使用する前に、`CDataRecoveryHandler`オブジェクトを呼び出す必要があります[CDataRecoveryHandler::Initialize](#initialize)します。

`CDataRecoveryHandler`クラスは、再起動マネージャーを密接に関連して`CDataRecoveryHandler`グローバル パラメーターに依存する`m_dwRestartManagerSupportFlags`します。 このパラメーターは、再起動マネージャーがどのようなアクセス許可と、アプリケーションと対話する方法を決定します。 再起動マネージャーを既存のアプリケーションに組み込むに割り当てる必要があります`m_dwRestartManagerSupportFlags`メイン アプリケーションのコンス トラクターで適切な値。 再起動マネージャーを使用する方法の詳細については、次を参照してください。[方法。再起動マネージャーのサポートを追加する](../../mfc/how-to-add-restart-manager-support.md)」をご覧ください。

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdatarecovery.h

##  <a name="autosavealldocumentinfo"></a>  CDataRecoveryHandler::AutosaveAllDocumentInfo

登録されている各ファイルの自動保存、`CDataRecoveryHandler`クラス。

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>戻り値

TRUE の場合、`CDataRecoveryHandler`保存されているすべてのドキュメント。任意のドキュメントが保存されていない場合は FALSE です。

### <a name="remarks"></a>Remarks

このメソッドは、ドキュメントを保存する必要がありますがない場合に TRUE を返します。 取得する場合、すべてのドキュメントを保存せず TRUE を返します、`CWinApp`または`CDocManager`のアプリケーションにエラーが生成されます。

このメソッドを使用して、AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART または AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL 設定する必要があります`m_dwRestartManagerSupportFlags`します。 詳細については、「[方法 :再起動マネージャーのサポートを追加する](../../mfc/how-to-add-restart-manager-support.md)」をご覧ください。

##  <a name="autosavedocumentinfo"></a>  CDataRecoveryHandler::AutosaveDocumentInfo

指定されたドキュメントの自動保存します。

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pDocument*|[in]ポインター、`CDocument`を保存します。|
|*bResetModifiedFlag*|[in]True を`CDataRecoveryHandler`考慮*pDocument* ; 変更するにはフレームワークを考慮する場合は false *pDocument*変更します。 このフラグの効果の詳細については「解説」を参照してください。|

### <a name="return-value"></a>戻り値

適切なフラグが設定されている場合は TRUE と*pDocument*は有効な`CDocument`オブジェクト。

### <a name="remarks"></a>Remarks

各`CDocument`オブジェクトが最後に保存してからそれが変更されているかを示すフラグ。 使用[CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified)このフラグの状態を判断します。 場合、`CDocument`が、最後に保存してから変更されていない`AutosaveDocumentInfo`そのドキュメントの自動保存されたファイルを削除します。 ドキュメントが最後に保存してから変更した場合は閉じても、ユーザーを閉じる前にドキュメントを保存するように求められます。

> [!NOTE]
>  使用して*bResetModifiedFlag*を変更するドキュメントの状態に変更されていない可能性がありますと、ユーザー データが失われる。 フレームワーク、ドキュメントが変更されていない場合、終了するプロンプトが表示されません、ユーザーを保存します。

このメソッドで例外をスロー、 [ASSERT](diagnostic-services.md#assert)マクロ場合*pDocument*は無効な`CDocument`オブジェクト。

このメソッドを使用して、AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART または AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL 設定する必要があります*m_dwRestartManagerSupportFlags*します。

##  <a name="cdatarecoveryhandler"></a>  CDataRecoveryHandler::CDataRecoveryHandler

`CDataRecoveryHandler` オブジェクトを構築します。

```
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,
    int nAutosaveInterval);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*dwRestartManagerSupportFlags*|[in]再起動マネージャーのオプションがサポートされていることを示します。|
|*nAutosaveInterval*|[in]自動保存までの時間。 このパラメーターは、ミリ秒単位です。|

### <a name="remarks"></a>Remarks

MFC フレームワークが自動的に作成、`CDataRecoveryHandler`を使用する場合、アプリケーションのオブジェクト、**新しいプロジェクト**ウィザード。 データの回復の動作をカスタマイズすることも、再起動マネージャーをする場合は、しない限り、作成しないようにする、`CDataRecoveryHandler`オブジェクト。

##  <a name="createdocumentinfo"></a>  CDataRecoveryHandler::CreateDocumentInfo

開いているドキュメントの一覧にドキュメントを追加します。

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pDocument*|[in]ポインター、`CDocument`します。 このメソッドは、このドキュメントの情報を作成します。`CDocument`します。|

### <a name="return-value"></a>戻り値

既定の実装では、TRUE を返します。

### <a name="remarks"></a>Remarks

このメソッドはチェック場合*pDocument*は、ドキュメントの一覧に既にドキュメントを追加する前にします。 場合*pDocument*は既にこのメソッドの一覧で、自動保存されたファイルに関連付けられている削除*pDocument*します。

このメソッドを使用して、AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART または AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL 設定する必要があります*m_dwRestartManagerSupportFlags*します。

##  <a name="deleteallautosavedfiles"></a>  CDataRecoveryHandler::DeleteAllAutosavedFiles

現在の自動保存されたファイルをすべて削除します。

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>戻り値

既定の実装を常に TRUE を返します。

##  <a name="deleteautosavedfile"></a>  CDataRecoveryHandler::DeleteAutosavedFile

指定された自動保存ファイルを削除します。

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*strAutosavedFile*|[in]自動保存されたファイル名を含む文字列。|

### <a name="return-value"></a>戻り値

既定の実装を常に TRUE を返します。

### <a name="remarks"></a>Remarks

このメソッドでは、自動保存されたファイルで削除できない場合は、一覧で、ファイルの名前を保存します。 デストラクター、`CDataRecoveryHandler`そのリストで指定された各自動保存されたファイルを削除しようとしています。

##  <a name="generateautosavefilename"></a>  CDataRecoveryHandler::GenerateAutosaveFileName

指定されたドキュメントのファイル名に関連付けられている自動保存ファイルの名前を生成します。

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>パラメーター

*strDocumentName*<br/>
[in]ドキュメント名を含む文字列。 `GenerateAutosaveFileName` このドキュメントの名前を使用すると、対応する自動保存ファイル名を生成します。

### <a name="return-value"></a>戻り値

自動保存ファイル名から生成された*strDocumentName*します。

### <a name="remarks"></a>Remarks

各ドキュメント名には、自動保存ファイル名と一対一のマッピングがいます。

##  <a name="getautosaveinterval"></a>  CDataRecoveryHandler::GetAutosaveInterval

自動保存の試行間隔を返します。

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>戻り値

自動保存の間隔をミリ秒数を試みます。

##  <a name="getautosavepath"></a>  CDataRecoveryHandler::GetAutosavePath

自動保存されたファイルのパスを返します。

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>戻り値

自動保存されたドキュメントの保存場所。

##  <a name="getdocumentlistname"></a>  CDataRecoveryHandler::GetDocumentListName

ドキュメントの名前を取得、`CDocument`オブジェクト。

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pDocument*|[in]ポインター、`CDocument`します。 `GetDocumentListName` このドキュメントの名前を取得`CDocument`します。|

### <a name="return-value"></a>戻り値

ドキュメント名から*pDocument*します。

### <a name="remarks"></a>Remarks

`CDataRecoveryHandler`ドキュメント名のキーとして使用*m_mapDocNameToAutosaveName*、 *m_mapDocNameToDocumentPtr*、および*m_mapDocNameToRestoreBool*します。 これらのパラメーターを有効にする、`CDataRecoveryHandler`を監視する`CDocument`オブジェクト、自動保存ファイル名、および自動保存設定します。

##  <a name="getnormaldocumenttitle"></a>  CDataRecoveryHandler::GetNormalDocumentTitle

指定した文書の通常のタイトルを取得します。

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pDocument*|[in]ポインター、`CDocument`します。|

### <a name="return-value"></a>戻り値

指定した文書の通常のタイトル。

### <a name="remarks"></a>Remarks

通常のドキュメントのタイトルは通常、パスを使用せず、ドキュメントのファイル名です。 これは、タイトル、**ファイル名**のフィールド、**名前を付けて保存** ダイアログ ボックス。

##  <a name="getrecovereddocumenttitle"></a>  CDataRecoveryHandler::GetRecoveredDocumentTitle

作成し、復元された文書のタイトルを返します。

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>パラメーター

*strDocumentTitle*<br/>
[in]通常のドキュメントのタイトル。

### <a name="return-value"></a>戻り値

回復したドキュメントのタイトル。

### <a name="remarks"></a>Remarks

既定では、ドキュメントの回復のタイトルには通常のタイトルを **[回復]** が追加されます。 回復したタイトルが、ユーザーに表示されるときに、`CDataRecoveryHandler`自動保存されたドキュメントを復元するユーザーのクエリを実行します。

##  <a name="getrestartidentifier"></a>  CDataRecoveryHandler::GetRestartIdentifier

アプリケーションの再起動の一意の識別子を取得します。

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>戻り値

一意の識別子を再起動します。

### <a name="remarks"></a>Remarks

再起動識別子は、アプリケーションの実行ごとに一意です。

`CDataRecoveryHandler`現在開いているドキュメントのレジストリに情報を格納します。 再起動の識別子を再起動マネージャーは、アプリケーションを終了するし、再起動、提供、`CDataRecoveryHandler`します。 `CDataRecoveryHandler`再起動識別子を使用して、以前開いているドキュメントの一覧を取得します。 これにより、`CDataRecoveryHandler`検索し、自動保存されたファイルを復元しようとします。

##  <a name="getsavedocumentinfoonidle"></a>  CDataRecoveryHandler::GetSaveDocumentInfoOnIdle

示すかどうか、`CDataRecoveryHandler`現在アイドル ループに対して自動保存を実行します。

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>戻り値

True、 `CDataRecoveryHandler` ; 現在アイドル ループの自動保存FALSE は、そうでないことを示します。

##  <a name="getshutdownbyrestartmanager"></a>  CDataRecoveryHandler::GetShutdownByRestartManager

再起動マネージャーのアプリケーションを終了する原因となったかどうかを示します。

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>戻り値

True の場合は再起動マネージャーによってアプリケーションが終了します。FALSE は、しないことを示します。

##  <a name="initialize"></a>  CDataRecoveryHandler::Initialize

`CDataRecoveryHandler` を初期化します。

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>戻り値

初期化に成功した場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

初期化プロセスでは、レジストリからの自動保存ファイルを保存するパスを読み込みます。 場合、`Initialize`メソッドは、このディレクトリを見つけることができませんかかどうか、パスが null の場合、`Initialize`失敗し、返します`FALSE`します。

使用[CDataRecoveryHandler::SetAutosavePath](#setautosavepath) 、アプリケーションが初期化された後に自動保存パスを変更する、`CDataRecoveryHandler`します。

`Initialize`メソッドも [次へ] の自動保存が発生したときに監視するためのタイマーを開始します。 使用[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval) 、アプリケーションが初期化された後に自動保存の間隔を変更する、`CDataRecoveryHandler`します。

##  <a name="queryrestoreautosaveddocuments"></a>  CDataRecoveryHandler::QueryRestoreAutosavedDocuments

各ドキュメントをユーザーにダイアログ ボックスを表示、`CDataRecoveryHandler`自動保存されます。 ダイアログ ボックスでは、ユーザーが自動保存されたドキュメントを復元するかどうかを判断します。

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>Remarks

アプリケーションが Unicode である場合は、このメソッドが表示されます、 [CTaskDialog](../../mfc/reference/ctaskdialog-class.md)をユーザーにします。 それ以外の場合、フレームワークを使用して[AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox)ユーザー照会します。

後`QueryRestoreAutosavedDocuments`すべての応答を収集、ユーザーから、メンバー変数に情報を格納、 *m_mapDocNameToRestoreBool*します。 このメソッドは、自動保存されたドキュメントを復元できません。

##  <a name="readopendocumentlist"></a>  CDataRecoveryHandler::ReadOpenDocumentList

レジストリから開いているドキュメントの一覧を読み込みます。

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>戻り値

TRUE が示す`ReadOpenDocumentList`レジストリから少なくとも 1 つのドキュメントの情報を読み込むFALSE は、ドキュメントの情報が読み込まれていないことを示します。

### <a name="remarks"></a>Remarks

この関数は、レジストリから開いているドキュメント情報が読み込まれ、メンバー変数に格納*m_mapDocNameToAutosaveName*します。

後`ReadOpenDocumentList`はすべてのデータを読み込み、レジストリからドキュメントの情報を削除します。

##  <a name="removedocumentinfo"></a>  CDataRecoveryHandler::RemoveDocumentInfo

開いているドキュメントの一覧から、指定されたドキュメントを削除します。

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pDocument*|[in]削除するドキュメントへのポインター。|

### <a name="return-value"></a>戻り値

TRUE の場合*pDocument*は、一覧から削除されましたエラーが発生した場合は FALSE です。

### <a name="remarks"></a>Remarks

ユーザーがドキュメントを閉じるときに、フレームワークは、開いているドキュメントの一覧から削除するのにこのメソッドを使用します。

場合`RemoveDocumentInfo`見つかりません*pDocument*で開いているドキュメントの一覧で、何も行われません、TRUE を返します。

このメソッドを使用して、AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 設定する必要があります*m_dwRestartManagerSupportFlags*します。

##  <a name="reopenpreviousdocuments"></a>  CDataRecoveryHandler::ReopenPreviousDocuments

以前に開かれているドキュメントを開きます。

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>戻り値

少なくとも 1 つのドキュメントが開いていた場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

このメソッドは、以前に開かれているドキュメントの最新の保存を開きます。 ドキュメントが保存されていない場合または自動保存、`ReopenPreviousDocuments`そのファイルの種類のテンプレートに基づく、空白の文書を開きます。

このメソッドを使用して、AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 設定する必要があります*m_dwRestartManagerSupportFlags*します。 このパラメーターが設定されていない場合`ReopenPreviousDocuments`何も実行し、FALSE を返します。

既に開いているドキュメントの一覧に格納されているドキュメントがない場合`ReopenPreviousDocuments`何も実行し、FALSE を返します。

##  <a name="restoreautosaveddocuments"></a>  CDataRecoveryHandler::RestoreAutosavedDocuments

ユーザー入力に基づいて、自動保存されたドキュメントを復元します。

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>戻り値

TRUE の場合は、このメソッドは、ドキュメントを正常に復元します。

### <a name="remarks"></a>Remarks

このメソッドを呼び出す[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)を復元する必要があるどのドキュメントをユーザーを決定します。 ユーザーでは、自動保存されたドキュメントを復元しない場合`RestoreAutosavedDocuments`自動保存ファイルを削除します。 それ以外の場合、`RestoreAutosavedDocuments`開いているドキュメントを自動保存されたバージョンに置き換えます。

このメソッドを使用して、AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES または AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES 設定する必要があります`m_dwRestartManagerSupportFlags`します。

##  <a name="saveopendocumentlist"></a>  CDataRecoveryHandler::SaveOpenDocumentList

現在開いているドキュメントの一覧を Windows レジストリに保存します。

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>戻り値

開いているドキュメントを保存することがない場合、または正常に保存された場合は TRUE です。 レジストリに保存するドキュメントが、エラーが発生したため、保存されていない場合は FALSE。

### <a name="remarks"></a>Remarks

再起動マネージャーの呼び出し`SaveOpenDocumentList`アプリケーションが予期せずが終了したとき、またはアップグレードするときに終了します。 使用して、アプリケーションが再起動したら、 [CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)開いているドキュメントの一覧を取得します。

このメソッドは、開いているドキュメントの一覧のみを保存します。 メソッド[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)ドキュメント自体の保存を担当します。

##  <a name="setautosaveinterval"></a>  CDataRecoveryHandler::SetAutosaveInterval

ミリ秒単位での自動保存のサイクルの間の時間を設定します。

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>パラメーター

*nAutosaveInterval*<br/>
[in]ミリ秒単位での新しい自動保存の間隔。

##  <a name="setautosavepath"></a>  CDataRecoveryHandler::SetAutosavePath

自動保存されたファイルが格納されるディレクトリを設定します。

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*strAutosavePath*|[in]自動保存ファイルが格納されるパス。|

### <a name="remarks"></a>Remarks

自動保存ディレクトリを変更するファイルは移動されません現在自動保存されます。

##  <a name="setrestartidentifier"></a>  CDataRecoveryHandler::SetRestartIdentifier

このインスタンスの再起動の一意の識別子を設定、`CDataRecoveryHandler`します。

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*strRestartIdentifier*|[in]再起動マネージャーの一意の識別子。|

### <a name="remarks"></a>Remarks

再起動マネージャーは、レジストリで開かれているドキュメントについての情報を記録します。 この情報は、再起動の一意の識別子を持つキーとして格納されます。 再起動の識別子は、アプリケーションの各インスタンスに対して一意であるため、アプリケーションの複数のインスタンスが予期せず終了可能性があり、再起動マネージャーが回復し、各します。

##  <a name="setsavedocumentinfoonidle"></a>  CDataRecoveryHandler::SetSaveDocumentInfoOnIdle

セットかどうか、`CDataRecoveryHandler`アイドル状態の現在のサイクル中に、開いているドキュメントの情報を Windows レジストリに保存します。

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*bSaveOnIdle*|[in]ドキュメントについては、現在のアイドル状態サイクル中に保存する場合は TRUE保存を実行する場合は FALSE。|

##  <a name="setshutdownbyrestartmanager"></a>  CDataRecoveryHandler::SetShutdownByRestartManager

再起動マネージャーによって、アプリケーションの以前の終了が発生したかどうかを設定します。

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*bShutdownByRestartManager*|[in]再起動マネージャーのアプリケーションを終了する原因となったことを指定する場合は TRUEもう 1 つの理由で、アプリケーションが終了していることを示す場合は FALSE。|

### <a name="remarks"></a>Remarks

フレームワークでは、前回の終了が予想されるかどうか、または再起動マネージャーによって開始されたかどうかに基づいて異なる方法では動作します。

##  <a name="updatedocumentinfo"></a>  CDataRecoveryHandler::UpdateDocumentInfo

そのユーザーが保存されるため、ドキュメントの情報を更新します。

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pDocument*|[in]保存されたドキュメントへのポインター。|

### <a name="return-value"></a>戻り値

このメソッドは、自動保存されたドキュメントを削除し、文書の情報を更新する場合は TRUE。エラーが発生した場合は FALSE です。

### <a name="remarks"></a>Remarks

ユーザーがドキュメントを保存すると、アプリケーションは、不要になったため、自動保存されたファイルを削除します。 `UpdateDocumentInfo` 呼び出すことによって、自動保存されたファイルを削除します[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)します。 `UpdateDocumentInfo` 情報を追加し、 *pDocument*の一覧に現在オープン ドキュメント`RemoveDocumentInfo`、その情報が保存されているを削除します。 ドキュメントが開かれたまま。

このメソッドを使用して、AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 設定する必要があります*m_dwRestartManagerSupportFlags*します。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[方法: 再起動マネージャーのサポートを追加する](../../mfc/how-to-add-restart-manager-support.md)
