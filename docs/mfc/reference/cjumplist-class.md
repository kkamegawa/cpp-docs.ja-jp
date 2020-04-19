---
title: CJumpList クラス
ms.date: 03/27/2019
f1_keywords:
- CJumpList
- AFXADV/CJumpList
- AFXADV/CJumpList::CJumpList
- AFXADV/CJumpList::AbortList
- AFXADV/CJumpList::AddDestination
- AFXADV/CJumpList::AddKnownCategory
- AFXADV/CJumpList::AddTask
- AFXADV/CJumpList::AddTasks
- AFXADV/CJumpList::AddTaskSeparator
- AFXADV/CJumpList::ClearAll
- AFXADV/CJumpList::ClearAllDestinations
- AFXADV/CJumpList::CommitList
- AFXADV/CJumpList::GetDestinationList
- AFXADV/CJumpList::GetMaxSlots
- AFXADV/CJumpList::GetRemovedItems
- AFXADV/CJumpList::InitializeList
- AFXADV/CJumpList::SetAppID
helpviewer_keywords:
- CJumpList [MFC], CJumpList
- CJumpList [MFC], AbortList
- CJumpList [MFC], AddDestination
- CJumpList [MFC], AddKnownCategory
- CJumpList [MFC], AddTask
- CJumpList [MFC], AddTasks
- CJumpList [MFC], AddTaskSeparator
- CJumpList [MFC], ClearAll
- CJumpList [MFC], ClearAllDestinations
- CJumpList [MFC], CommitList
- CJumpList [MFC], GetDestinationList
- CJumpList [MFC], GetMaxSlots
- CJumpList [MFC], GetRemovedItems
- CJumpList [MFC], InitializeList
- CJumpList [MFC], SetAppID
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
ms.openlocfilehash: 9296912c97b1efb5f7cbd1ed9f769d0222d5f85c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392571"
---
# <a name="cjumplist-class"></a>CJumpList クラス

A`CJumpList`タスク バーのアイコンを右クリックしたときに表示されるショートカットの一覧を示します。

## <a name="syntax"></a>構文

```
class CJumpList;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CJumpList::CJumpList](#cjumplist)|`CJumpList` オブジェクトを構築します。|
|[CJumpList:: ~ CJumpList](#_dtorcjumplist)|`CJumpList` オブジェクトを破棄します。|

|名前|説明|
|----------|-----------------|
|[CJumpList::AbortList](#abortlist)|コミットせずリスト構築トランザクションを中止します。|
|[CJumpList::AddDestination](#adddestination)|オーバーロードされます。 一覧には、変換先を追加します。|
|[CJumpList::AddKnownCategory](#addknowncategory)|一覧には、既知のカテゴリを追加します。|
|[CJumpList::AddTask](#addtask)|オーバーロードされます。 正規のタスク カテゴリには、項目を追加します。|
|[CJumpList::AddTasks](#addtasks)|正規のタスク カテゴリには、項目を追加します。|
|[CJumpList::AddTaskSeparator](#addtaskseparator)|タスク間の区切り記号を追加します。|
|[CJumpList::ClearAll](#clearall)|すべてのタスクと変換先の現在のインスタンスに追加された削除`CJumpList`これまでにします。|
|[CJumpList::ClearAllDestinations](#clearalldestinations)|現在のインスタンスに追加されたすべての変換先を削除します。`CJumpList`これまでにします。|
|[CJumpList::CommitList](#commitlist)|リスト構築トランザクションを終了し、報告された一覧をコミットに関連付けられているストア (ここではレジストリです。)|
|[CJumpList::GetDestinationList](#getdestinationlist)|ターゲット リストへのインターフェイス ポインターを取得します。|
|[CJumpList::GetMaxSlots](#getmaxslots)|呼び出し元アプリケーションの移行先のメニューで表示できるカテゴリ ヘッダーを含む項目の最大数を取得します。|
|[CJumpList::GetRemovedItems](#getremoveditems)|表す項目の配列を返しますでは、変換先を削除します。|
|[CJumpList::InitializeList](#initializelist)|リスト構築トランザクションを開始します。|
|[CJumpList::SetAppID](#setappid)|構築されるリストのアプリケーション ユーザー モデル ID を設定します。|

## <a name="inheritance-hierarchy"></a>継承階層

[CJumpList](../../mfc/reference/cjumplist-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxadv.h

##  <a name="_dtorcjumplist"></a>  CJumpList:: ~ CJumpList

`CJumpList` オブジェクトを破棄します。

```
~CJumpList();
```

##  <a name="abortlist"></a>  CJumpList::AbortList

コミットせずリスト構築トランザクションを中止します。

```
void AbortList();
```

### <a name="remarks"></a>Remarks

このメソッドを呼び出すのと同じ効果を破棄する`CJumpList`呼び出さず`CommitList`します。

##  <a name="adddestination"></a>  CJumpList::AddDestination

一覧には、変換先を追加します。

```
BOOL AddDestination(
    LPCTSTR lpcszCategoryName,
    LPCTSTR strDestinationPath);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellItem* pShellItem);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellLink* pShellLink);
```

### <a name="parameters"></a>パラメーター

*lpcszCategoryName*<br/>
カテゴリ名を指定します。 指定したカテゴリが存在しない場合は、それが作成されます。

*strDestinationPath*<br/>
コピー先ファイルへのパスを指定します。

*strCategoryName*<br/>
カテゴリ名を指定します。 指定したカテゴリが存在しない場合は、それが作成されます。

*pShellItem*<br/>
シェル項目が追加されている変換先を表すを指定します。

*pShellLink*<br/>
シェルのリンクが追加されている変換先を表すを指定します。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

インスタンス`CJumpList`追加の変換先を内部的に蓄積され、それらをコミット`CommitList`します。

##  <a name="addknowncategory"></a>  CJumpList::AddKnownCategory

一覧には、既知のカテゴリを追加します。

```
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```

### <a name="parameters"></a>パラメーター

*category*<br/>
既知のカテゴリの種類を指定します。 KDC_RECENT、または KDC_KNOWN のいずれかを指定できます。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

既知のカテゴリは、利用頻度および最近使ったもの カテゴリを使用するすべてのアプリケーションに対して私たちが自動的に計算する`SHAddToRecentDocs`(または、直接に使用されることに、シェルを使用すると一部のシナリオで、アプリケーションの代わりに呼び出すが、)。

##  <a name="addtask"></a>  CJumpList::AddTask

正規のタスク カテゴリには、項目を追加します。

```
BOOL AddTask(
    LPCTSTR strTargetExecutablePath,
    LPCTSTR strCommandLineArgs,
    LPCTSTR strTitle,
    LPCTSTR strIconLocation,
    int iIconIndex);

BOOL AddTask(IShellLink* pShellLink);
```

### <a name="parameters"></a>パラメーター

*strTargetExecutablePath*<br/>
タスクのターゲット パスを指定します。

*strCommandLineArgs*<br/>
指定された実行可能ファイルのコマンドライン引数を指定*strTargetExecutablePath*します。

*strTitle*<br/>
ターゲット リストに表示されるタスクの名前。

*strIconLocation*<br/>
タイトルと共に移行先のリストに表示されるアイコンの場所です。

*iIconIndex*<br/>
アイコンのインデックス。

*pShellLink*<br/>
追加するタスクを表現するシェルのリンク。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

インスタンス`CJumpList`指定したタスクの累積し、中に、ターゲット リストに追加`CommitList`します。 タスク項目は、アプリケーションの移行先のメニューの下部にあるカテゴリに表示されます。 このカテゴリは他のすべてのカテゴリに優先される UI でいっぱいになったときにします。

##  <a name="addtasks"></a>  CJumpList::AddTasks

正規のタスク カテゴリには、項目を追加します。

```
BOOL AddTasks(IObjectArray* pObjectCollection);
```

### <a name="parameters"></a>パラメーター

*pObjectCollection*<br/>
追加するタスクのコレクション。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

CJumpList のインスタンスは、指定したタスクを蓄積され、中に、ターゲット リストに追加します`CommitList`します。 タスク項目は、アプリケーションの移行先のメニューの下部にあるカテゴリに表示されます。 このカテゴリは他のすべてのカテゴリに優先される UI でいっぱいになったときにします。

##  <a name="addtaskseparator"></a>  CJumpList::AddTaskSeparator

タスク間の区切り記号を追加します。

```
BOOL AddTaskSeparator();
```

### <a name="return-value"></a>戻り値

、成功した場合は 0 以外でない場合は 0。

##  <a name="cjumplist"></a>  CJumpList::CJumpList

`CJumpList` オブジェクトを構築します。

```
CJumpList(BOOL bAutoCommit = TRUE);
```

### <a name="parameters"></a>パラメーター

*bAutoCommit*<br/>
このパラメーターが FALSE の場合、リストがデストラクターで自動的にコミットされません。

##  <a name="clearall"></a>  CJumpList::ClearAll

すべてのタスクと変換先の現在のインスタンスに追加された削除`CJumpList`これまでにします。

```
void ClearAll();
```

### <a name="remarks"></a>Remarks

このメソッドは、クリアし、すべてのデータと内部インターフェイスを解放します。

##  <a name="clearalldestinations"></a>  CJumpList::ClearAllDestinations

これまでに CJumpList の現在のインスタンスに追加されたすべての変換先を削除します。

```
void ClearAllDestinations();
```

### <a name="remarks"></a>Remarks

他の変換先、再度追加して変換先 ボックスの一覧のビルドの現在のセッションでこれまでに追加されたすべての変換先を削除する必要がある場合は、この関数を呼び出します。 場合、内部`ICustomDestinationList`されましたが、初期化が中断したアライブします。

##  <a name="commitlist"></a>  CJumpList::CommitList

リスト構築トランザクションを終了し、関連付けられているストア (ここではレジストリ) に報告されたリストをコミットします。

```
BOOL CommitList();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

コミットはアトミックです。 エラーが、コミットに失敗した場合に返されます。  ときに`CommitList`を呼び出すと、現在削除された項目の一覧をクリーンアップします。 リストの構築のアクティブなトランザクションがあるないように、オブジェクトをリセットするこのメソッドを呼び出します。 一覧を更新する`BeginList`もう一度呼び出す必要があります。

##  <a name="getdestinationlist"></a>  CJumpList::GetDestinationList

ターゲット リストへのインターフェイス ポインターを取得します。

```
ICustomDestinationList* GetDestinationList();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

ジャンプ リストは初期化されていないか、コミットまたは中止されていますが場合、返される値は NULL になります。

##  <a name="getmaxslots"></a>  CJumpList::GetMaxSlots

呼び出し元アプリケーションの移行先のメニューで表示できるカテゴリ ヘッダーを含む項目の最大数を取得します。

```
UINT GetMaxSlots() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

アプリケーションでは、さまざまな項目と組み合わせてこの値になるまでカテゴリ ヘッダーがレポートのみ可能性があります。 場合に呼び出す`AppendCategory`、 `AppendKnownCategory`、または`AddUserTasks`この数を超える、エラーが返されます。

##  <a name="getremoveditems"></a>  CJumpList::GetRemovedItems

表す項目の配列を返しますでは、変換先を削除します。

```
IObjectArray* GetRemovedItems();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

削除された変換先は、ジャンプ リストの初期化中に取得されます。 新しい変換先のリストを生成するときに、最初の追跡データ削除の一覧の列挙子によって返されるすべての項目をオフにすると、削除された変換先の一覧を処理するアプリケーションが必要です。 アプリケーションが、現在の呼び出しをトランザクションにだけ削除された項目を提供しようとしています。 場合`BeginList`開始されると、その項目を再度追加したメソッドの呼び出しは失敗、アプリケーションが削除されたリストを尊重しすることを確認します。

##  <a name="initializelist"></a>  CJumpList::InitializeList

リスト構築トランザクションを開始します。

```
BOOL InitializeList();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

ポインターを取得する場合を除き、このメソッドを明示的に呼び出す必要はありません`ICustomDestinationList`を使用して`GetDestinationList`を使用して、使用可能なスロット数`GetMaxSlots`、またはを使用して削除された項目のリストを`GetRemovedItems`します。

##  <a name="setappid"></a>  CJumpList::SetAppID

構築されるリストのアプリケーション ユーザー モデル ID を設定します。

```
void SetAppID(LPCTSTR strAppID);
```

### <a name="parameters"></a>パラメーター

*strAppID*<br/>
アプリケーション ユーザー モデル ID を指定する文字列

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
