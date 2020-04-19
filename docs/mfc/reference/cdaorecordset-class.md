---
title: CDaoRecordset クラス
ms.date: 08/27/2018
f1_keywords:
- CDaoRecordset
- AFXDAO/CDaoRecordset
- AFXDAO/CDaoRecordset::CDaoRecordset
- AFXDAO/CDaoRecordset::AddNew
- AFXDAO/CDaoRecordset::CanAppend
- AFXDAO/CDaoRecordset::CanBookmark
- AFXDAO/CDaoRecordset::CancelUpdate
- AFXDAO/CDaoRecordset::CanRestart
- AFXDAO/CDaoRecordset::CanScroll
- AFXDAO/CDaoRecordset::CanTransact
- AFXDAO/CDaoRecordset::CanUpdate
- AFXDAO/CDaoRecordset::Close
- AFXDAO/CDaoRecordset::Delete
- AFXDAO/CDaoRecordset::DoFieldExchange
- AFXDAO/CDaoRecordset::Edit
- AFXDAO/CDaoRecordset::FillCache
- AFXDAO/CDaoRecordset::Find
- AFXDAO/CDaoRecordset::FindFirst
- AFXDAO/CDaoRecordset::FindLast
- AFXDAO/CDaoRecordset::FindNext
- AFXDAO/CDaoRecordset::FindPrev
- AFXDAO/CDaoRecordset::GetAbsolutePosition
- AFXDAO/CDaoRecordset::GetBookmark
- AFXDAO/CDaoRecordset::GetCacheSize
- AFXDAO/CDaoRecordset::GetCacheStart
- AFXDAO/CDaoRecordset::GetCurrentIndex
- AFXDAO/CDaoRecordset::GetDateCreated
- AFXDAO/CDaoRecordset::GetDateLastUpdated
- AFXDAO/CDaoRecordset::GetDefaultDBName
- AFXDAO/CDaoRecordset::GetDefaultSQL
- AFXDAO/CDaoRecordset::GetEditMode
- AFXDAO/CDaoRecordset::GetFieldCount
- AFXDAO/CDaoRecordset::GetFieldInfo
- AFXDAO/CDaoRecordset::GetFieldValue
- AFXDAO/CDaoRecordset::GetIndexCount
- AFXDAO/CDaoRecordset::GetIndexInfo
- AFXDAO/CDaoRecordset::GetLastModifiedBookmark
- AFXDAO/CDaoRecordset::GetLockingMode
- AFXDAO/CDaoRecordset::GetName
- AFXDAO/CDaoRecordset::GetParamValue
- AFXDAO/CDaoRecordset::GetPercentPosition
- AFXDAO/CDaoRecordset::GetRecordCount
- AFXDAO/CDaoRecordset::GetSQL
- AFXDAO/CDaoRecordset::GetType
- AFXDAO/CDaoRecordset::GetValidationRule
- AFXDAO/CDaoRecordset::GetValidationText
- AFXDAO/CDaoRecordset::IsBOF
- AFXDAO/CDaoRecordset::IsDeleted
- AFXDAO/CDaoRecordset::IsEOF
- AFXDAO/CDaoRecordset::IsFieldDirty
- AFXDAO/CDaoRecordset::IsFieldNull
- AFXDAO/CDaoRecordset::IsFieldNullable
- AFXDAO/CDaoRecordset::IsOpen
- AFXDAO/CDaoRecordset::Move
- AFXDAO/CDaoRecordset::MoveFirst
- AFXDAO/CDaoRecordset::MoveLast
- AFXDAO/CDaoRecordset::MoveNext
- AFXDAO/CDaoRecordset::MovePrev
- AFXDAO/CDaoRecordset::Open
- AFXDAO/CDaoRecordset::Requery
- AFXDAO/CDaoRecordset::Seek
- AFXDAO/CDaoRecordset::SetAbsolutePosition
- AFXDAO/CDaoRecordset::SetBookmark
- AFXDAO/CDaoRecordset::SetCacheSize
- AFXDAO/CDaoRecordset::SetCacheStart
- AFXDAO/CDaoRecordset::SetCurrentIndex
- AFXDAO/CDaoRecordset::SetFieldDirty
- AFXDAO/CDaoRecordset::SetFieldNull
- AFXDAO/CDaoRecordset::SetFieldValue
- AFXDAO/CDaoRecordset::SetFieldValueNull
- AFXDAO/CDaoRecordset::SetLockingMode
- AFXDAO/CDaoRecordset::SetParamValue
- AFXDAO/CDaoRecordset::SetParamValueNull
- AFXDAO/CDaoRecordset::SetPercentPosition
- AFXDAO/CDaoRecordset::Update
- AFXDAO/CDaoRecordset::m_bCheckCacheForDirtyFields
- AFXDAO/CDaoRecordset::m_nFields
- AFXDAO/CDaoRecordset::m_nParams
- AFXDAO/CDaoRecordset::m_pDAORecordset
- AFXDAO/CDaoRecordset::m_pDatabase
- AFXDAO/CDaoRecordset::m_strFilter
- AFXDAO/CDaoRecordset::m_strSort
helpviewer_keywords:
- CDaoRecordset [MFC], CDaoRecordset
- CDaoRecordset [MFC], AddNew
- CDaoRecordset [MFC], CanAppend
- CDaoRecordset [MFC], CanBookmark
- CDaoRecordset [MFC], CancelUpdate
- CDaoRecordset [MFC], CanRestart
- CDaoRecordset [MFC], CanScroll
- CDaoRecordset [MFC], CanTransact
- CDaoRecordset [MFC], CanUpdate
- CDaoRecordset [MFC], Close
- CDaoRecordset [MFC], Delete
- CDaoRecordset [MFC], DoFieldExchange
- CDaoRecordset [MFC], Edit
- CDaoRecordset [MFC], FillCache
- CDaoRecordset [MFC], Find
- CDaoRecordset [MFC], FindFirst
- CDaoRecordset [MFC], FindLast
- CDaoRecordset [MFC], FindNext
- CDaoRecordset [MFC], FindPrev
- CDaoRecordset [MFC], GetAbsolutePosition
- CDaoRecordset [MFC], GetBookmark
- CDaoRecordset [MFC], GetCacheSize
- CDaoRecordset [MFC], GetCacheStart
- CDaoRecordset [MFC], GetCurrentIndex
- CDaoRecordset [MFC], GetDateCreated
- CDaoRecordset [MFC], GetDateLastUpdated
- CDaoRecordset [MFC], GetDefaultDBName
- CDaoRecordset [MFC], GetDefaultSQL
- CDaoRecordset [MFC], GetEditMode
- CDaoRecordset [MFC], GetFieldCount
- CDaoRecordset [MFC], GetFieldInfo
- CDaoRecordset [MFC], GetFieldValue
- CDaoRecordset [MFC], GetIndexCount
- CDaoRecordset [MFC], GetIndexInfo
- CDaoRecordset [MFC], GetLastModifiedBookmark
- CDaoRecordset [MFC], GetLockingMode
- CDaoRecordset [MFC], GetName
- CDaoRecordset [MFC], GetParamValue
- CDaoRecordset [MFC], GetPercentPosition
- CDaoRecordset [MFC], GetRecordCount
- CDaoRecordset [MFC], GetSQL
- CDaoRecordset [MFC], GetType
- CDaoRecordset [MFC], GetValidationRule
- CDaoRecordset [MFC], GetValidationText
- CDaoRecordset [MFC], IsBOF
- CDaoRecordset [MFC], IsDeleted
- CDaoRecordset [MFC], IsEOF
- CDaoRecordset [MFC], IsFieldDirty
- CDaoRecordset [MFC], IsFieldNull
- CDaoRecordset [MFC], IsFieldNullable
- CDaoRecordset [MFC], IsOpen
- CDaoRecordset [MFC], Move
- CDaoRecordset [MFC], MoveFirst
- CDaoRecordset [MFC], MoveLast
- CDaoRecordset [MFC], MoveNext
- CDaoRecordset [MFC], MovePrev
- CDaoRecordset [MFC], Open
- CDaoRecordset [MFC], Requery
- CDaoRecordset [MFC], Seek
- CDaoRecordset [MFC], SetAbsolutePosition
- CDaoRecordset [MFC], SetBookmark
- CDaoRecordset [MFC], SetCacheSize
- CDaoRecordset [MFC], SetCacheStart
- CDaoRecordset [MFC], SetCurrentIndex
- CDaoRecordset [MFC], SetFieldDirty
- CDaoRecordset [MFC], SetFieldNull
- CDaoRecordset [MFC], SetFieldValue
- CDaoRecordset [MFC], SetFieldValueNull
- CDaoRecordset [MFC], SetLockingMode
- CDaoRecordset [MFC], SetParamValue
- CDaoRecordset [MFC], SetParamValueNull
- CDaoRecordset [MFC], SetPercentPosition
- CDaoRecordset [MFC], Update
- CDaoRecordset [MFC], m_bCheckCacheForDirtyFields
- CDaoRecordset [MFC], m_nFields
- CDaoRecordset [MFC], m_nParams
- CDaoRecordset [MFC], m_pDAORecordset
- CDaoRecordset [MFC], m_pDatabase
- CDaoRecordset [MFC], m_strFilter
- CDaoRecordset [MFC], m_strSort
ms.assetid: 2322067f-1027-4662-a5d7-aa2fc7488630
ms.openlocfilehash: 96118645aa656e97fcb93a0fd223045208ab03a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206360"
---
# <a name="cdaorecordset-class"></a>CDaoRecordset クラス

データ ソースから選択された 1 組のレコードセットを表現します。

## <a name="syntax"></a>構文

```
class CDaoRecordset : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDaoRecordset::CDaoRecordset](#cdaorecordset)|`CDaoRecordset` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDaoRecordset::AddNew](#addnew)|新しいレコードを追加する準備をします。 呼び出す[Update](#update)追加を完了します。|
|[CDaoRecordset::CanAppend](#canappend)|使用してレコード セットに新しいレコードを追加する場合は 0 以外を返します、 [AddNew](#addnew)メンバー関数。|
|[CDaoRecordset::CanBookmark](#canbookmark)|レコード セットは、ブックマークをサポートしている場合、0 以外の値を返します。|
|[CDaoRecordset::CancelUpdate](#cancelupdate)|ために、保留中の更新をキャンセル、[Edit](#edit)または[AddNew](#addnew)操作。|
|[CDaoRecordset::CanRestart](#canrestart)|場合は 0 以外の値を返します[Requery](#requery)レコード セットのクエリを再実行を呼び出すことができます。|
|[CDaoRecordset::CanScroll](#canscroll)|レコードをスクロールする場合は 0 以外を返します。|
|[CDaoRecordset::CanTransact](#cantransact)|データ ソースは、トランザクションをサポートしている場合、0 以外の値を返します。|
|[CDaoRecordset::CanUpdate](#canupdate)|レコード セットを更新する場合は 0 以外を返します (することができますを追加、更新、またはレコードを削除) します。|
|[CDaoRecordset::Close](#close)|レコード セットを閉じます。|
|[CDaoRecordset::Delete](#delete)|レコード セットから現在のレコードを削除します。 削除後は、別のレコードに明示的にスクロールする必要があります。|
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|レコード セットのフィールド データ メンバーと、データ ソースに対応するレコード間を双方向) でデータを交換するには、呼び出されます。 レコード フィールド エクス (チェンジ DFX) をを実装 DAO します。|
|[CDaoRecordset::Edit](#edit)|現在のレコードへの変更の準備を行います。 呼び出す`Update`編集を完了します。|
|[CDaoRecordset::FillCache](#fillcache)|すべての塗りつぶしまたは ODBC データ ソースからデータを含むレコード セット オブジェクトのローカル キャッシュの一部です。|
|[CDaoRecordset::Find](#find)|最初に、[次へ] を検索、特定の文字列を指定された条件と、そのレコードを現在のレコードを満たすダイナセット タイプのレコード セット内の前、または最後の位置。|
|[CDaoRecordset::FindFirst](#findfirst)|ダイナセット型またはレコードを指定された条件と、そのレコードを現在のレコードを満たす最初のレコードを検索します。|
|[CDaoRecordset::FindLast](#findlast)|ダイナセット型またはレコードを指定された条件と、そのレコードを現在のレコードを満たすには、最後のレコードを検索します。|
|[CDaoRecordset::FindNext](#findnext)|ダイナセット型またはレコードを指定された条件と、そのレコードを現在のレコードを満たすには、次のレコードを検索します。|
|[CDaoRecordset::FindPrev](#findprev)|ダイナセット型またはレコードを指定された条件と、そのレコードを現在のレコードを満たすには、前のレコードを検索します。|
|[CDaoRecordset::GetAbsolutePosition](#getabsoluteposition)|レコード セット オブジェクトの現在のレコードのレコード数を返します。|
|[CDaoRecordset::GetBookmark](#getbookmark)|レコードのブックマークを表す値を返します。|
|[CDaoRecordset::GetCacheSize](#getcachesize)|ODBC データ ソースからローカルにキャッシュされたデータを含むダイナセット タイプのレコード セット内のレコードの数を示す値を返します。|
|[CDaoRecordset::GetCacheStart](#getcachestart)|キャッシュするレコード セット内の最初のレコードのブックマークを示す値を返します。|
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|返します、 `CString` 、インデックス付きのテーブル型で使用される最近にインデックスの名前を含む`CDaoRecordset`します。|
|[CDaoRecordset::GetDateCreated](#getdatecreated)|基になるベース テーブルの日付と時刻を返します、`CDaoRecordset`オブジェクトが作成されました|
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|基になるベース テーブルの設計に加えられた最新の変更日時を返します、`CDaoRecordset`オブジェクト。|
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|既定のデータ ソースの名前を返します。|
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|実行する既定の SQL 文字列を取得するには、呼び出されます。|
|[CDaoRecordset::GetEditMode](#geteditmode)|現在のレコードの編集状態を示す値を返します。|
|[CDaoRecordset::GetFieldCount](#getfieldcount)|レコード セット内のフィールドの数を表す値を返します。|
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|レコード セットの特定の種類のフィールドの詳細についての情報を返します。|
|[CDaoRecordset::GetFieldValue](#getfieldvalue)|レコード セット内のフィールドの値を返します。|
|[CDaoRecordset::GetIndexCount](#getindexcount)|レコード セットを基になるテーブル内のインデックスの数を取得します。|
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|さまざまな種類のインデックスの情報を返します。|
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|最もが最近追加またはレコードの更新を決定するために使用します。|
|[CDaoRecordset::GetLockingMode](#getlockingmode)|編集中に有効になっているロックの種類を示す値を返します。|
|[CDaoRecordset::GetName](#getname)|返します、`CString`レコード セットの名前を格納します。|
|[CDaoRecordset::GetParamValue](#getparamvalue)|基になる DAOParameter オブジェクトに格納されている指定されたパラメーターの現在の値を取得します。|
|[CDaoRecordset::GetPercentPosition](#getpercentposition)|現在のレコードのレコードの合計数に対する割合としての位置を返します。|
|[CDaoRecordset::GetRecordCount](#getrecordcount)|レコード セット オブジェクトにアクセスするレコードの数を返します。|
|[CDaoRecordset::GetSQL](#getsql)|レコード セットのレコードを選択するために使用する SQL 文字列を取得します。|
|[CDaoRecordset::GetType](#gettype)|レコード セットの種類を決定するために呼び出されます。 テーブル型、ダイナセット タイプ、またはスナップショットの種類。|
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|返します、`CString`フィールドに入力されたデータを検証する値を格納します。|
|[CDaoRecordset::GetValidationText](#getvalidationtext)|検証規則が満たされていない場合に表示されるテキストを取得します。|
|[CDaoRecordset::IsBOF](#isbof)|レコード セットは、最初のレコードの前に位置付けられている場合は 0 以外を返します。 現在のレコードはありません。|
|[CDaoRecordset::IsDeleted](#isdeleted)|レコード セットが削除されたレコードに配置されている場合は 0 以外を返します。|
|[CDaoRecordset::IsEOF](#iseof)|レコード セットは、後の最後のレコードに位置付けられている場合は 0 以外を返します。 現在のレコードはありません。|
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|現在のレコードで指定されたフィールドが変更されている場合、0 以外の値を返します。|
|[CDaoRecordset::IsFieldNull](#isfieldnull)|現在のレコードで指定されたフィールドが Null (値がない) 場合、0 以外の値を返します。|
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|現在のレコードで指定されたフィールドに設定できます Null (値がない) 場合は 0 以外を返します。|
|[CDaoRecordset::IsOpen](#isopen)|場合は 0 以外の値を返します[オープン](#open)が既に呼び出されています。|
|[CDaoRecordset::Move](#move)|いずれかの方向で現在のレコードから指定された数のレコードをレコード セットを配置します。|
|[CDaoRecordset::MoveFirst](#movefirst)|現在のレコードをレコード セットの最初のレコードに位置付けます。|
|[CDaoRecordset::MoveLast](#movelast)|現在のレコードをレコード セットの最後のレコードに位置付けます。|
|[CDaoRecordset::MoveNext](#movenext)|現在のレコードをレコード セットの次のレコードに位置付けます。|
|[CDaoRecordset::MovePrev](#moveprev)|現在のレコードをレコード セットの前のレコードに位置付けます。|
|[CDaoRecordset::Open](#open)|テーブル、ダイナセット、またはスナップショットから新しいレコード セットを作成します。|
|[CDaoRecordset::Requery](#requery)|選択したレコードを更新するには、もう一度、レコード セットのクエリを実行します。|
|[CDaoRecordset::Seek](#seek)|インデックス付きのテーブル型のレコード セット オブジェクトを現在のインデックスと、そのレコードを現在のレコードの指定した条件を満たすレコードを検索します。|
|[CDaoRecordset::SetAbsolutePosition](#setabsoluteposition)|レコード セット オブジェクトの現在のレコードのレコード数を設定します。|
|[CDaoRecordset::SetBookmark](#setbookmark)|指定されたブックマークを含むレコードをレコード セットに配置します。|
|[CDaoRecordset::SetCacheSize](#setcachesize)|ODBC データ ソースからローカルにキャッシュされたデータを含むダイナセット タイプのレコード セット内のレコードの数を示す値を設定します。|
|[CDaoRecordset::SetCacheStart](#setcachestart)|キャッシュするレコード セット内の最初のレコードのブックマークを示す値を設定します。|
|[CDaoRecordset::SetCurrentIndex](#setcurrentindex)|テーブル型のレコード セットのインデックスを設定すると呼ばれます。|
|[CDaoRecordset::SetFieldDirty](#setfielddirty)|変更されたものとしては、現在のレコードで指定したフィールドをマークします。|
|[CDaoRecordset::SetFieldNull](#setfieldnull)|Null (値を持たない) を現在のレコードで指定されたフィールドの値を設定します。|
|[たび](#setfieldvalue)|レコード セット内のフィールドの値を設定します。|
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|Null にレコード セット内のフィールドの値を設定します。 (値を持たない)。|
|[CDaoRecordset::SetLockingMode](#setlockingmode)|編集中に有効にするロックの種類を示す値を設定します。|
|[CDaoRecordset::SetParamValue](#setparamvalue)|基になる DAOParameter オブジェクトに格納されている指定されたパラメーターの現在の値を設定します。|
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|指定されたパラメーターの現在の値を Null (値がない) に設定します。|
|[CDaoRecordset::SetPercentPosition](#setpercentposition)|レコード セット内のレコードの合計数に対する割合に対応する場所を現在のレコードの位置を設定します。|
|[CDaoRecordset::Update](#update)|完了すると、`AddNew`または`Edit`データ ソースの新規または編集されたデータを保存することで操作します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CDaoRecordset::m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|フィールドの変更は自動的にマークするかどうかを示すフラグが含まれています。|
|[CDaoRecordset::m_nFields](#m_nfields)|レコード セット クラスのフィールド データ メンバーの数と、データ ソースからレコード セットが選択した列の数が含まれています。|
|[CDaoRecordset::m_nParams](#m_nparams)|レコード セット クラスでパラメーターのデータ メンバーの数が含まれています — レコード セットのクエリで渡されるパラメーターの数|
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|レコード セット オブジェクトを基になる DAO インターフェイスへのポインター。|
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|この結果セットのソース データベースです。 ポインターが含まれています、 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)オブジェクト。|
|[CDaoRecordset::m_strFilter](#m_strfilter)|SQL の構築に使用される文字列を含む**WHERE**ステートメント。|
|[CDaoRecordset::m_strSort](#m_strsort)|SQL の構築に使用される文字列を含む**ORDER BY**ステートメント。|

## <a name="remarks"></a>Remarks

「レコード セット」と呼ばれる`CDaoRecordset`オブジェクトは、次の 3 つのフォームで使用できます。

- テーブル型のレコード セットは、確認、追加、変更、または単一のデータベース テーブルからレコードを削除する際、ベース テーブルを表します。

- ダイナセット タイプのレコード セットは、更新可能なレコードを持つクエリの結果です。 これらのレコード セットは、確認、追加、変更、または、基になるデータベース テーブルまたはテーブルからレコードを削除に使用できるレコードのセットです。 ダイナセット タイプのレコード セットは、データベース内の 1 つまたは複数のテーブルのフィールドを含めることができます。

- スナップショットの種類のレコード セットは、一連のデータの検索やレポートの生成に使用できるレコードの静的なコピーです。 これらのレコード セットは、データベース内の 1 つまたは複数のテーブルのフィールドを含めることができますが、更新することはできません。

レコード セットの各フォームは、レコード セットを開くときに固定されたレコードのセットを表します。 テーブル型のレコード セットまたはダイナセット タイプのレコード セット内のレコードをスクロールすると、他のユーザーまたはアプリケーションで他のレコード セットのいずれか、レコード セットが開かれた後に、レコードに加えられた変更が反映されます。 (スナップショットの種類のレコード セットを更新できません。)使用することができます`CDaoRecordset`直接からのアプリケーション固有のレコード セット クラスを派生または`CDaoRecordset`します。 することができます。

- レコードをスクロールします。

- インデックスを設定しを使用してレコードを探して[シーク](#seek)(テーブル型のレコード セットのみ)。

- 文字列比較に基づいてレコードを検索:"<「、」\<="、「=」、"> ="、または">"(ダイナセット タイプおよびスナップショット タイプのレコード セット)。

- レコードを更新し、(スナップショットの種類のレコード セット) を除くロック モードを指定します。

- データ ソースで利用可能なからを選択するレコードを制限するレコード セットをフィルター処理します。

- レコード セットを並べ替えます。

- 実行時までわからない情報を使用して選択をカスタマイズするレコード セットをパラメーター化します。

クラス`CDaoRecordset`のクラスに似たインターフェイスを提供`CRecordset`します。 主な違いは、そのクラス`CDaoRecordset`OLE に基づくデータ アクセス オブジェクト (DAO) を介してデータにアクセスします。 クラス`CRecordset`DBMS の Open Database Connectivity (ODBC) と ODBC ドライバーを介して、DBMS にアクセスします。

> [!NOTE]
> DAO データベース クラスは、ベースの開いているデータベースの接続 (ODBC) で MFC データベース クラスとは異なります。 DAO データベース クラスの名前には、"CDao"プレフィックスが付いています。 DAO クラス; で ODBC データ ソースのアクセスをできます。DAO クラスは、一般には、Microsoft Jet データベース エンジンに固有であるため、優れた機能の機能を提供します。

使用するか`CDaoRecordset`直接からクラスを派生または`CDaoRecordset`します。 いずれの場合も、レコード セット クラスを使用するデータベースを開くし、コンス トラクターへのポインターを渡して、レコード セット オブジェクトを構築、`CDaoDatabase`オブジェクト。 構築することも、`CDaoRecordset`オブジェクトし、MFC、一時パスワードが作成できるように`CDaoDatabase`オブジェクト。 呼び出してレコード セットの[オープン](#open)メンバー関数、オブジェクトは、テーブル型のレコード セット、ダイナセット タイプのレコード セット、またはスナップショットの種類のレコード セットかどうかを指定します。 呼び出す`Open`データベースからデータを選択し、最初のレコードを取得します。

レコードをスクロールし、それを操作するには、オブジェクトのメンバー関数とデータ メンバーを使用します。 使用可能な操作は、オブジェクトは、テーブル型のレコード セット、ダイナセット タイプのレコード セット、または、スナップショットの種類のレコード セットかどうかと、更新可能なと読み取り専用であるかによって異なります-これは、データベースまたは Open Database Connectivity (ODBC) の機能に依存。データ ソース。 可能性がありますが変更または追加された後のレコードを更新する、`Open`呼び出し、オブジェクトの[Requery](#requery)メンバー関数。 オブジェクトの`Close`メンバー関数をそれが完了したら、オブジェクトを破棄します。

`CDaoRecordset` タイプ セーフな C++ のメンバーの読み取りとレコードのフィールドの更新をサポートするために DAO レコード フィールド エクス (チェンジ DFX) を使用して、`CDaoRecordset`または`CDaoRecordset`-クラスを派生します。 DFX メカニズムの使用を使用せず、データベース内の列の動的バインドを実装することも[GetFieldValue](#getfieldvalue)と[いる](#setfieldvalue)します。

関連情報については、「レコード セット オブジェクト」DAO のヘルプ トピックを参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdao.h

##  <a name="addnew"></a>  CDaoRecordset::AddNew

テーブル型またはダイナセット タイプのレコード セットに新しいレコードを追加するには、このメンバー関数を呼び出します。

```
virtual void AddNew();
```

### <a name="remarks"></a>Remarks

レコードのフィールドが最初に Null です。 (データベース用語では、Null「値を持たない」手段と C++ では NULL の場合と同じではありません)。操作を完了するには、呼び出す必要がある、 [Update](#update)メンバー関数。 `Update` データ ソースに変更を保存します。

> [!CAUTION]
>  レコードを編集して別のレコードを呼び出さずにスクロールし、 `Update`、変更は警告なしに失われます。

呼び出すことによって、ダイナセット タイプのレコード セットにレコードを追加するかどうかは[AddNew](#addnew)、レコードがレコード セットの表示とがいずれかに表示される新しい基になるテーブルに含まれる`CDaoRecordset`オブジェクト。

新しいレコードの位置は、レコード セットの種類によって異なります。

- ダイナセット タイプでは、新しいレコードを挿入する位置のレコード セットは保証されません。 この動作は、パフォーマンス、および同時実行の上の理由から Microsoft Jet 3.0 に変更します。 目標は、新しく追加されたレコードを現在のレコードには、最後に変更されたレコードのブックマークを取得し、そのブックマークに移動します。

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- インデックスが指定されているタイプのレコード、並べ替え順序において適切な場所でレコードが返されます。 インデックスが指定されていない場合は、レコード セットの末尾に新しいレコードが返されます。

レコードは、使用する前にカレント`AddNew`を最新の状態します。 現在、新しいレコードを作成して、レコード セットは、ブックマーク、呼び出しをサポートしている場合[SetBookmark](#setbookmark)を LastModified プロパティの設定の基になる DAO レコード セット オブジェクトで識別されるブックマーク。 これは、追加したレコード内のカウンター (自動インクリメント) フィールドの値を決定するために役立ちます。 詳細については、次を参照してください。 [GetLastModifiedBookmark](#getlastmodifiedbookmark)します。

データベースでは、トランザクションをサポートする場合は、`AddNew`トランザクションの一部を呼び出します。 トランザクションの詳細については、クラスを参照してください。 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)します。 呼び出す必要がありますので注意[CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans)呼び出す前に`AddNew`します。

呼び出すことはできません`AddNew`レコード セットを持つ[オープン](#open)メンバー関数が呼び出されていません。 A`CDaoException`を呼び出す場合にスローされる`AddNew`のレコード セットに追加することはできません。 呼び出すことによって、レコード セットは更新可能かどうかを判断する[CanAppend](#canappend)します。

フレームワークでは、フィールド データ メンバーに DAO レコード フィールド エクス (チェンジ DFX) メカニズムによって、データ ソースのレコードに記述が変更されました。 フィールドの値を変更すると、通常フィールド ダーティ設定、自動的に呼び出す必要はめったにありません[き](#setfielddirty)が、自分でことがありますようにすることも、列が明示的に更新または挿入に関係なくどのような値のフィールドのデータ メンバーです。 DFX メカニズムは、の使用も採用されています。**PSEUDO NULL**します。 詳細については、[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)を参照してください。

ダブル バッファリング機構を使用しない場合、フィールドの値を変更して自動的に設定しませんフィールド ダーティとして。 この場合は、ダーティ フィールドを明示的に設定する必要があります。 含まれているフラグ[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)このフィールドの自動チェックを制御します。

> [!NOTE]
> レコードは、ダブル バッファリングを行う場合 (つまり、フィールドの自動チェックが有効)、呼び出す`CancelUpdate`メンバー変数を前の値に復元されます`AddNew`または`Edit`が呼び出されました。

関連情報については、「AddNew メソッド」、「CancelUpdate メソッド」、「LastModified プロパティ」および「EditMode プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="canappend"></a>  CDaoRecordset::CanAppend

呼び出すことによって新しいレコードを追加する前に開かれたレコード セットができるかどうかを判断するには、このメンバー関数を呼び出す、 [AddNew](#addnew)メンバー関数。

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>戻り値

レコード セットが新しいレコードを追加できる場合は 0 以外それ以外の場合 0 を返します。 `CanAppend` 読み取り専用レコード セットを開いた場合 0 を返します。

### <a name="remarks"></a>Remarks

関連情報については、「DAO ヘルプの「メソッドの追加」」を参照してください。

##  <a name="canbookmark"></a>  CDaoRecordset::CanBookmark

以前に開かれたレコード セットが個別にブックマークを使用してレコードをマークすることをできるかどうかを判断するには、このメンバー関数を呼び出します。

```
BOOL CanBookmark();
```

### <a name="return-value"></a>戻り値

以外の場合は、レコード セットは、ブックマーク、それ以外の場合 0 をサポートしています。

### <a name="remarks"></a>Remarks

Microsoft Jet データベース エンジンのテーブルに完全に基づくレコード セットを使用している場合は、順方向専用のスクロール レコード セットとしてフラグが設定されたスナップショットの種類のレコード セットで以外のブックマークが使用できます。 その他のデータベース製品 (外部の ODBC データ ソース) はブックマークをサポートしていません。

関連情報については、DAO ヘルプの「ブックマークを設定プロパティ」を参照してください。

##  <a name="cancelupdate"></a>  CDaoRecordset::CancelUpdate

`CancelUpdate`メンバー関数は、ために、保留中の更新をキャンセル、[Edit](#edit)または[AddNew](#addnew)操作。

```
virtual void CancelUpdate();
```

### <a name="remarks"></a>Remarks

たとえば、アプリケーションを呼び出す、`Edit`または`AddNew`メンバー関数が呼び出されていないと[Update](#update)、`CancelUpdate`後に加えられた変更を取り消します`Edit`または`AddNew`が呼び出されました。

> [!NOTE]
>  レコードは、ダブル バッファリングを行う場合 (つまり、フィールドの自動チェックが有効)、呼び出す`CancelUpdate`メンバー変数を前の値に復元されます`AddNew`または`Edit`が呼び出されました。

存在する場合ありません`Edit`または`AddNew`操作保留中、 `CancelUpdate` MFC 例外をスローすると、します。 呼び出す、 [GetEditMode](#geteditmode)メンバー関数をキャンセルできる保留中の操作があるかどうかを判断します。

関連情報については、「CancelUpdate メソッド」DAO ヘルプのトピックを参照してください。

##  <a name="canrestart"></a>  CDaoRecordset::CanRestart

レコード セットでは、(そのレコードを更新) するためには、そのクエリを呼び出すことによって再起動できるかどうかを判断するには、このメンバー関数を呼び出す、`Requery`メンバー関数。

```
BOOL CanRestart();
```

### <a name="return-value"></a>戻り値

0 以外の値`Requery`レコード セットのクエリを再び、それ以外の場合 0 を実行するということができます。

### <a name="remarks"></a>Remarks

テーブル型のレコード セットをサポートしていない`Requery`します。

場合`Requery`は呼び出しがサポートされていない[Close](#close)し[Open](#open)データを更新します。 呼び出すことができます`Requery`オブジェクトを更新するレコード セットの基になるパラメーターのクエリ パラメーターの値が変更された後です。

関連情報については、「再起動可能なプロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="canscroll"></a>  CDaoRecordset::CanScroll

レコード セットでは、スクロールできるかどうかを判断するには、このメンバー関数を呼び出します。

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>戻り値

以外の場合は 0 それ以外の場合、レコードをスクロールすることができます。

### <a name="remarks"></a>Remarks

呼び出す場合[オープン](#open)で`dbForwardOnly`、レコード セットは前方スクロールのみできます。

関連情報については、"配置、現在のレコード ポインターと DAO"DAO ヘルプのトピックを参照してください。

##  <a name="cantransact"></a>  CDaoRecordset::CanTransact

レコード セットにトランザクションができるかどうかを判断するには、このメンバー関数を呼び出します。

```
BOOL CanTransact();
```

### <a name="return-value"></a>戻り値

基になるデータ ソースは 0 それ以外の場合、トランザクションをサポートしている場合 0 以外の値。

### <a name="remarks"></a>Remarks

関連情報については、「トランザクションのプロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="canupdate"></a>  CDaoRecordset::CanUpdate

レコード セットを更新できるかどうかを判断するには、このメンバー関数を呼び出します。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>戻り値

レコード セットを更新する場合は 0 以外 (追加、更新、およびレコードの削除)、それ以外の場合に 0 です。

### <a name="remarks"></a>Remarks

レコード セットは、その基になるデータ ソースが読み取り専用の場合、または指定した場合読み取り専用である可能性があります`dbReadOnly`の*nOptions*を呼び出した場合[オープン](#open)のレコード セット。

関連情報については、「AddNew メソッド」、「メソッドの編集」、「メソッドの削除」、"Update Method"、および DAO ヘルプの「更新可能なプロパティ」トピックを参照してください。

##  <a name="cdaorecordset"></a>  CDaoRecordset::CDaoRecordset

`CDaoRecordset` オブジェクトを構築します。

```
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>パラメーター

*pDatabase*<br/>
ポインターが含まれています、 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)オブジェクトまたは値が NULL です。 NULL でない場合、`CDaoDatabase`オブジェクトの`Open`データ ソースに接続するメンバー関数が呼び出されていない、レコード セットが、独自の中を開くしようとしています。[開く](#open)を呼び出します。 Null チェックを実行する場合、`CDaoDatabase`オブジェクトが構築されからレコード セット クラスを派生するかどうかに指定したデータ ソース情報を使用して接続されている`CDaoRecordset`します。

### <a name="remarks"></a>Remarks

使用するか`CDaoRecordset`直接または、アプリケーション固有のクラスから派生した`CDaoRecordset`します。 ClassWizard を使用して、レコード セット クラスを派生させることができます。

> [!NOTE]
>  派生した場合、`CDaoRecordset`クラス、派生クラスは、独自のコンス トラクターを指定する必要があります。 派生クラスのコンス トラクターでコンス トラクターを呼び出す`CDaoRecordset::CDaoRecordset`に沿った適切なパラメーターを渡します。

レコード セットのコンス トラクターに NULL を渡す、`CDaoDatabase`オブジェクトが構築され、自動的に結合します。 これは、構築し、接続を必要としないの便利なショートカットを`CDaoDatabase`レコード セットを作成する前にオブジェクト。 場合、`CDaoDatabase`オブジェクトが開いていない、 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)オブジェクトは、既定のワークスペースを使用するのも作成されます。 詳細については、次を参照してください。 [CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase)します。

##  <a name="close"></a>  CDaoRecordset::Close

閉じる、`CDaoRecordset`オブジェクトが関連付けられているデータベースで開いているレコード セットのコレクションから削除します。

```
virtual void Close();
```

### <a name="remarks"></a>Remarks

`Close`を破棄しません、`CDaoRecordset`オブジェクトを呼び出すことによって、オブジェクトを再利用できる`Open`同じデータ ソースまたは別のデータ ソース。

保留中のすべて[AddNew](#addnew)または[編集](#edit)ステートメントが取り消されると、および保留中のトランザクションがすべてロールバックされます。 保留中の追加や変更を保持する場合は、呼び出す[Update](#update)を呼び出す前に`Close`の各レコード セット。

呼び出すことができます`Open`呼び出した後でもう一度`Close`します。 これにより、レコード セット オブジェクトを再利用できます。 呼び出すことよりも優れたです[Requery](#requery)、可能な場合。

関連情報については、「Close メソッド」DAO ヘルプのトピックを参照してください。

##  <a name="delete"></a>  CDaoRecordset::Delete

開いているダイナセット型またはテーブル型のレコード セット オブジェクトの現在のレコードを削除するには、このメンバー関数を呼び出します。

```
virtual void Delete();
```

### <a name="remarks"></a>Remarks

削除が成功した後、レコード セットのフィールド データ メンバーは、Null 値に設定され、レコード セットのナビゲーションのメンバー関数のいずれかを明示的に呼び出す必要があります ([Move](#move)、[Seek](#seek)、 [SetBookmark](#setbookmark)など)、削除されたレコードから移動するためにします。 レコード セットからレコードを削除するときに必要があります、現在のレコード、レコード セットを呼び出す前に`Delete`、それ以外の例外がスローされます。

`Delete` 現在のレコードを削除し、アクセスできなくなります。 編集または削除されたレコードを使用することはできません、現在は残ります。 別のレコードに移動するとすることはできません、削除したレコード現在もう一度です。

> [!CAUTION]
>  レコード セットは更新可能である必要がありする必要がありますがある有効なレコードの現在のレコード セットを呼び出すとき`Delete`します。 たとえば、レコードを削除しても、呼び出す前に新しいレコードをスクロールしません`Delete`、もう一度`Delete`がスローされます、 [CDaoException](../../mfc/reference/cdaoexception-class.md)します。

トランザクションを使用してを呼び出す場合は、レコードを復元できます、 [CDaoWorkspace::Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback)メンバー関数。 ベース テーブルが主テーブルが連鎖的には、リレーションシップを削除、現在のレコードを削除すると、外部テーブル内 1 つまたは複数のレコードも削除可能性があります。 詳細については、DAO のヘルプで削除定義"cascade"を参照してください。

異なり`AddNew`と`Edit`への呼び出し`Delete`への呼び出しによってに従わない`Update`します。

関連情報については、「AddNew メソッド」、「メソッドの編集」、「メソッドの削除」、"Update Method"、および DAO ヘルプの「更新可能なプロパティ」トピックを参照してください。

##  <a name="dofieldexchange"></a>  CDaoRecordset::DoFieldExchange

フレームワークは、自動的に、レコード セット オブジェクトのフィールド データ メンバーと、データ ソースの現在のレコードの対応する列の間のデータを交換するには、このメンバー関数を呼び出します。

```
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>パラメーター

*pFX*<br/>
ポインターが含まれています、`CDaoFieldExchange`オブジェクト。 フレームワークは、フィールド交換操作のコンテキストを指定する、このオブジェクトは、既に設定があります。

### <a name="remarks"></a>Remarks

また、レコード セットの選択用の SQL ステートメントの文字列内のパラメーターのプレース ホルダーに存在する場合、パラメーターのデータ メンバーをバインドします。 DAO レコード フィールド エクス チェンジ (DFX) と呼ばれるフィールドのデータの交換が双方向で機能します。 レコード セット オブジェクトをデータ ソースのレコードと、データ ソースのレコードのフィールドをレコード セット オブジェクトのフィールド データ メンバーから。 列を動的にバインドする場合は、実装する必要はありません`DoFieldExchange`します。

唯一のアクションを実装するために通常必要`DoFieldExchange`クラスは、派生したレコード セットを ClassWizard でクラスを作成し、フィールド データ メンバーの名前とデータ型を指定します。 ClassWizard を書き込むパラメーターのデータ メンバーを指定するコードを追加することも可能性があります。 すべてのフィールドに動的にバインドする場合は、この関数がアクティブになりませんパラメーター データ メンバーを指定しない限り、します。

ClassWizard でレコード セットの派生クラスを宣言するときに書き込まれますのオーバーライドを`DoFieldExchange`次の例のようにします。

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

##  <a name="edit"></a>  CDaoRecordset::Edit

現在のレコードを変更できるようにするには、このメンバー関数を呼び出します。

```
virtual void Edit();
```

### <a name="remarks"></a>Remarks

呼び出すと、`Edit`メンバー関数は、現在のレコードのフィールドに加えられた変更は、コピー バッファーにコピーされます。 レコードに必要な変更を行った後で呼び出す`Update`変更を保存します。 `Edit` レコード セットのデータ メンバーの値を保存します。 呼び出す場合`Edit`を呼び出して、変更を行う`Edit`1 つ目の前に、レコードの値を復元する、もう一度`Edit`呼び出し。

> [!CAUTION]
>  レコードを編集し、最初に呼び出さず、他のレコードに移動する操作を実行すると`Update`、変更は警告なしに失われます。 さらに、レコード セットまたは親データベースを閉じた場合は、警告なし、編集されたレコードが破棄されます。

場合によっては、Null (データを含まない) ようにすることで、列を更新する場合があります。 これを行うには、呼び出す`SetFieldNull`マーク フィールドを Null の場合は true のパラメーターを使ってこれもにより、更新する列。 場合は、フィールドの値が変更されていない場合でも、データ ソースに書き込む、呼び出し`SetFieldDirty`TRUE の場合のパラメーターを使用します。 これは、フィールド値が Null 場合でも機能します。

フレームワークでは、フィールド データ メンバーに DAO レコード フィールド エクス (チェンジ DFX) メカニズムによって、データ ソースのレコードに記述が変更されました。 フィールドの値を変更すると、通常フィールド ダーティ設定、自動的に呼び出す必要はめったにありません[き](#setfielddirty)が、自分でことがありますようにすることも、列が明示的に更新または挿入に関係なくどのような値のフィールドのデータ メンバーです。 DFX メカニズムは、の使用も採用されています。**PSEUDO NULL**します。 詳細については、次を参照してください。 [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)します。

ダブル バッファリング機構を使用しない場合、フィールドの値を変更して自動的に設定しませんフィールド ダーティとして。 この場合は、ダーティ フィールドを明示的に設定する必要があります。 含まれているフラグ[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)このフィールドの自動チェックを制御します。

レコードの時点からロックされたまま、レコード セット オブジェクトがマルチ ユーザー環境で排他ロックされると、`Edit`更新が完了するまでに使用されます。 レコード セットがロックされる場合、レコードがロックされているし、データベースで更新される直前に、編集前のレコードと比較します。 呼び出されるので、レコードが変更された場合`Edit`、`Update`操作が失敗して、MFC は、例外をスローします。 ロック モードを変更する`SetLockingMode`します。

> [!NOTE]
>  オプティミスティック ロックは常に、ODBC およびインストール可能な ISAM などの外部データベース形式で使用します。

現在のレコードを呼び出した後は、最新の状態`Edit`します。 呼び出す`Edit`、現在のレコードが必要があります。 現在のレコードが存在しない場合、またはレコード セットがオープン テーブル型またはダイナセット タイプのレコード セット オブジェクトを参照していない場合は、例外が発生します。 呼び出す`Edit`により、`CDaoException`が次の状況でスローされます。

- 現在のレコードはありません。

- データベースまたはレコード セットは読み取り専用です。

- レコードのフィールドは、更新可能ではありません。

- データベースまたはレコード セットは、別のユーザーによって排他的に開かれました。

- 別のユーザーは、レコードを含むページをロックされています。

データ ソースは、トランザクションをサポートする場合は、`Edit`トランザクションの一部を呼び出します。 呼び出す必要がありますので注意`CDaoWorkspace::BeginTrans`呼び出す前に`Edit`後、レコード セットが開かれているとします。 その呼び出し元にも注意してください`CDaoWorkspace::CommitTrans`通話に代わるものでない`Update`を完了する、`Edit`操作。 トランザクションの詳細については、クラスを参照してください。`CDaoWorkspace`します。

関連情報については、「AddNew メソッド」、「メソッドの編集」、「メソッドの削除」、"Update Method"、および DAO ヘルプの「更新可能なプロパティ」トピックを参照してください。

##  <a name="fillcache"></a>  CDaoRecordset::FillCache

指定された数のレコード セットからレコードをキャッシュするには、このメンバー関数を呼び出します。

```
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>パラメーター

*pSize*<br/>
キャッシュを埋めるために行の数を指定します。 このパラメーターを省略した場合、値は、基になる DAO オブジェクトの CacheSize プロパティの設定によって決まります。

*pBookmark*<br/>
A [COleVariant](../../mfc/reference/colevariant-class.md)ブックマークを指定します。 キャッシュはこのブックマークで示されたレコードから開始されます。 このパラメーターを省略した場合、キャッシュは、基になる DAO オブジェクトの CacheStart プロパティで示されたレコードから開始されます。

### <a name="remarks"></a>Remarks

キャッシュすると、取得、またはリモート サーバーからデータをフェッチするアプリケーションのパフォーマンスが向上します。 キャッシュは、直前に、サーバーからフェッチされた前提としているデータが再度要求されるアプリケーションの実行中にデータを保持するローカル メモリ内の領域が。 ときにデータを要求すると、Microsoft Jet データベース エンジンのキャッシュ データをまずチェック時間がかかると、サーバーからのフェッチではなく。 非 ODBC データ ソースにデータ キャッシュを使用しても何も起こりませんように、データがキャッシュに保存されません。

フェッチされるレコードを格納するキャッシュを待機しているのではなく明示的を入力できます、キャッシュ、いつでも呼び出すことによって、`FillCache`メンバー関数。 これは、方法は、高速なため、キャッシュの充てんに`FillCache`一度に 1 つずつ代わりに、一度に複数のレコードをフェッチします。 たとえば、画面にレコードが表示されているときに、アプリケーション呼び出しを作成できます`FillCache`を次の画面いっぱいのレコードをフェッチします。

レコード セット オブジェクトを使用してアクセスする任意の ODBC データベースには、ローカル キャッシュを持つことができます。 キャッシュを作成するには、リモート データ ソースからレコード セット オブジェクトを開くを呼び出して、`SetCacheSize`と`SetCacheStart`レコード セットのメンバー関数。 場合*lSize*と*lBookmark*部分的または完全に指定した範囲外の範囲を作成`SetCacheSize`と`SetCacheStart`、この範囲外のレコード セットの部分は無視されないです。キャッシュに読み込まれます。 場合`FillCache`要求よりも多くのレコードが、リモート データ ソースに残ります、残りのレコードのみがフェッチされ、例外はスローされません。

キャッシュからフェッチされたレコードでは、他のユーザーがデータ ソースに同時に行われた変更は反映されません。

`FillCache` キャッシュされていないレコードだけをフェッチします。 キャッシュされたすべてのデータの更新プログラムを強制的に、`SetCacheSize`メンバー関数を*lSize*パラメーターを 0、呼び出し`SetCacheSize`を使用して、 *lSize*パラメーターは、キャッシュのサイズに等しい最初に要求して、呼び出して`FillCache`します。

関連情報については、DAO のヘルプで「FillCache メソッド」を参照してください。

##  <a name="find"></a>  CDaoRecordset::Find

比較演算子を使用して、ダイナセット、またはスナップショットの種類のレコード セット内で特定の文字列を検索するには、このメンバー関数を呼び出します。

```
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>パラメーター

*lFindType*<br/>
必要な検索操作の種類を示す値。 次の値を指定できます。

- AFX_DAO_NEXT では、一致する文字列の次の場所を検索します。

- AFX_DAO_PREV では、一致する文字列の前の場所を検索します。

- AFX_DAO_FIRST では、一致する文字列の最初の位置を検索します。

- AFX_DAO_LAST では、一致する文字列の最後の場所を検索します。

*lpszFilter*<br/>
文字列式 (など、**WHERE**語を除く SQL ステートメントの句**WHERE**) レコードを検索するために使用します。 例:

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>戻り値

一致するレコードが見つかった場合、それ以外の場合 0 0 以外の値。

### <a name="remarks"></a>Remarks

最初に、[次へ] を検索する文字列の前、または最後のインスタンス。 `Find` 仮想関数をこのメソッドをオーバーライドし、独自の実装を追加できます。 `FindFirst`、 `FindLast`、 `FindNext`、および`FindPrev`メンバー関数の呼び出し、`Find`メンバー関数を使用できるように`Find`すべての検索操作の動作を制御します。

テーブル型のレコード セットのレコードを検索、呼び出し、[Seek](#seek)メンバー関数。

> [!TIP]
>  レコードがある場合より効果的な一連の小さな`Find`になります。 一般に、および ODBC のデータでは特に、目的のレコードだけを取得する新しいクエリを作成することをお勧めします。

関連情報についてを参照してください"FindFirst、FindLast、FindNext、FindPrevious メソッド"DAO のヘルプします。

##  <a name="findfirst"></a>  CDaoRecordset::FindFirst

指定した条件に一致する最初のレコードを検索するには、このメンバー関数を呼び出します。

```
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>パラメーター

*lpszFilter*<br/>
文字列式 (など、**WHERE**語を除く SQL ステートメントの句**WHERE**) レコードを検索するために使用します。

### <a name="return-value"></a>戻り値

一致するレコードが見つかった場合、それ以外の場合 0 0 以外の値。

### <a name="remarks"></a>Remarks

`FindFirst`メンバー関数は、レコード セットの先頭から検索し、レコード セットの末尾に検索が開始されます。

レコード間を移動する移動操作の 1 つのレコードを検索 (だけではなく特定の条件を満たしているもの) を使用してすべてを含める場合は。 テーブル型のレコード セットのレコードを検索、呼び出し、`Seek`メンバー関数。

現在のレコード ポインターは、決められた条件に一致するレコードが見つからない場合、`FindFirst`は 0 を返します。 レコード セットには、条件を満たす 1 つ以上のレコードが含まれている場合`FindFirst`最初に見つかった検索`FindNext`と次の出現箇所を検索します。

> [!CAUTION]
>  現在のレコードを編集する場合に呼び出すことによって、変更を保存することを確認して、`Update`別のレコードに移動する前に、メンバー関数。 更新することがなく別のレコードに移動すると、変更内容は警告なしに失われます。

`Find`メンバー関数の場所から、次の表で指定した方向での検索します。

|検索操作|開始|検索の方向|
|---------------------|-----------|----------------------|
|`FindFirst`|レコード セットの先頭|レコード セットの末尾|
|`FindLast`|レコード セットの末尾|レコード セットの先頭|
|`FindNext`|現在のレコード|レコード セットの末尾|
|`FindPrevious`|現在のレコード|レコード セットの先頭|

> [!NOTE]
>  呼び出すと`FindLast`、Microsoft Jet データベース エンジンがこれが既に行われていない場合、検索を開始する前に、レコード セットが完全に設定します。 最初の検索は、後続の検索よりも長くかかる場合があります。

検索操作のいずれかを使用ない呼び出しと同じ`MoveFirst`または`MoveNext`、ただし、これだけです、最初または次のレコード現在しなくても、条件を指定します。 移動操作で検索操作に従うことができます。

検索操作を使用する場合は、次に留意してください。

- 場合`Find`返します 0 以外の場合、現在のレコードが定義されていません。 この場合は、有効なレコードには、現在のレコード ポインターを配置する必要があります。

- 検索操作は、順方向専用スクロール スナップショットの種類のレコードを使用できません。

- 米国の日付形式 (1 か月-日-年) を使用する必要があります Microsoft Jet データベース エンジンの米国版を使用していない場合でも、日付を含むフィールドを検索するときそれ以外の場合、一致するレコードが見つからない可能性があります。

- ODBC データベースで大きなダイナセットを使用する場合は、検索操作が遅いこと、大きなレコード セットを使用する場合に特に検出可能性があります。 SQL クエリを使用してパフォーマンスを向上させることができますとカスタマイズ**ORDERBY**または**WHERE**句、パラメーター クエリ、または`CDaoQuerydef`インデックス付きの特定のレコードを取得するオブジェクト。

関連情報についてを参照してください"FindFirst、FindLast、FindNext、FindPrevious メソッド"DAO のヘルプします。

##  <a name="findlast"></a>  CDaoRecordset::FindLast

指定した条件に一致する最後のレコードを検索するには、このメンバー関数を呼び出します。

```
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>パラメーター

*lpszFilter*<br/>
文字列式 (など、**WHERE**語を除く SQL ステートメントの句**WHERE**) レコードを検索するために使用します。

### <a name="return-value"></a>戻り値

一致するレコードが見つかった場合、それ以外の場合 0 0 以外の値。

### <a name="remarks"></a>Remarks

`FindLast`メンバー関数は、レコード セットの末尾に検索し、レコード セットの先頭に向かって後方検索を開始します。

レコード間を移動する移動操作の 1 つのレコードを検索 (だけではなく特定の条件を満たしているもの) を使用してすべてを含める場合は。 テーブル型のレコード セットのレコードを検索、呼び出し、`Seek`メンバー関数。

現在のレコード ポインターは、決められた条件に一致するレコードが見つからない場合、`FindLast`は 0 を返します。 レコード セットには、条件を満たす 1 つ以上のレコードが含まれている場合`FindFirst`最初に見つかった検索`FindNext`と、最初に見つかった位置の後に次の出現箇所を検索します。

> [!CAUTION]
>  現在のレコードを編集する場合に呼び出すことによって、変更を保存することを確認して、`Update`別のレコードに移動する前に、メンバー関数。 更新することがなく別のレコードに移動すると、変更内容は警告なしに失われます。

検索操作のいずれかを使用ない呼び出しと同じ`MoveFirst`または`MoveNext`、ただし、これだけです、最初または次のレコード現在しなくても、条件を指定します。 移動操作で検索操作に従うことができます。

検索操作を使用する場合は、次に留意してください。

- 場合`Find`返します 0 以外の場合、現在のレコードが定義されていません。 この場合は、有効なレコードには、現在のレコード ポインターを配置する必要があります。

- 検索操作は、順方向専用スクロール スナップショットの種類のレコードを使用できません。

- 米国の日付形式 (1 か月-日-年) を使用する必要があります Microsoft Jet データベース エンジンの米国版を使用していない場合でも、日付を含むフィールドを検索するときそれ以外の場合、一致するレコードが見つからない可能性があります。

- ODBC データベースで大きなダイナセットを使用する場合は、検索操作が遅いこと、大きなレコード セットを使用する場合に特に検出可能性があります。 SQL クエリを使用してパフォーマンスを向上させることができますとカスタマイズ**ORDERBY**または**WHERE**句、パラメーター クエリ、または`CDaoQuerydef`インデックス付きの特定のレコードを取得するオブジェクト。

関連情報についてを参照してください"FindFirst、FindLast、FindNext、FindPrevious メソッド"DAO のヘルプします。

##  <a name="findnext"></a>  CDaoRecordset::FindNext

指定した条件に一致する次のレコードを検索するには、このメンバー関数を呼び出します。

```
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>パラメーター

*lpszFilter*<br/>
文字列式 (など、**WHERE**語を除く SQL ステートメントの句**WHERE**) レコードを検索するために使用します。

### <a name="return-value"></a>戻り値

一致するレコードが見つかった場合、それ以外の場合 0 0 以外の値。

### <a name="remarks"></a>Remarks

`FindNext`メンバー関数は、現在のレコードには、その検索を開始し、レコード セットの末尾に検索します。

レコード間を移動する移動操作の 1 つのレコードを検索 (だけではなく特定の条件を満たしているもの) を使用してすべてを含める場合は。 テーブル型のレコード セットのレコードを検索、呼び出し、`Seek`メンバー関数。

現在のレコード ポインターは、決められた条件に一致するレコードが見つからない場合、`FindNext`は 0 を返します。 レコード セットには、条件を満たす 1 つ以上のレコードが含まれている場合`FindFirst`最初に見つかった検索`FindNext`と次の出現箇所を検索します。

> [!CAUTION]
>  現在のレコードを編集する場合に呼び出すことによって、変更を保存することを確認して、`Update`別のレコードに移動する前に、メンバー関数。 更新することがなく別のレコードに移動すると、変更内容は警告なしに失われます。

検索操作のいずれかを使用ない呼び出しと同じ`MoveFirst`または`MoveNext`、ただし、これだけです、最初または次のレコード現在しなくても、条件を指定します。 移動操作で検索操作に従うことができます。

検索操作を使用する場合は、次に留意してください。

- 場合`Find`返します 0 以外の場合、現在のレコードが定義されていません。 この場合は、有効なレコードには、現在のレコード ポインターを配置する必要があります。

- 検索操作は、順方向専用スクロール スナップショットの種類のレコードを使用できません。

- 米国の日付形式 (1 か月-日-年) を使用する必要があります Microsoft Jet データベース エンジンの米国版を使用していない場合でも、日付を含むフィールドを検索するときそれ以外の場合、一致するレコードが見つからない可能性があります。

- ODBC データベースで大きなダイナセットを使用する場合は、検索操作が遅いこと、大きなレコード セットを使用する場合に特に検出可能性があります。 SQL クエリを使用してパフォーマンスを向上させることができますとカスタマイズ**ORDERBY**または**WHERE**句、パラメーター クエリ、または`CDaoQuerydef`インデックス付きの特定のレコードを取得するオブジェクト。

関連情報についてを参照してください"FindFirst、FindLast、FindNext、FindPrevious メソッド"DAO のヘルプします。

##  <a name="findprev"></a>  CDaoRecordset::FindPrev

指定した条件に一致する以前のレコードを検索するには、このメンバー関数を呼び出します。

```
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>パラメーター

*lpszFilter*<br/>
文字列式 (など、**WHERE**語を除く SQL ステートメントの句**WHERE**) レコードを検索するために使用します。

### <a name="return-value"></a>戻り値

一致するレコードが見つかった場合、それ以外の場合 0 0 以外の値。

### <a name="remarks"></a>Remarks

`FindPrev`メンバー関数は、現在のレコードには、その検索を開始し、レコード セットの先頭に向かって逆方向に検索します。

レコード間を移動する移動操作の 1 つのレコードを検索 (だけではなく特定の条件を満たしているもの) を使用してすべてを含める場合は。 テーブル型のレコード セットのレコードを検索、呼び出し、`Seek`メンバー関数。

現在のレコード ポインターは、決められた条件に一致するレコードが見つからない場合、`FindPrev`は 0 を返します。 レコード セットには、条件を満たす 1 つ以上のレコードが含まれている場合`FindFirst`最初に見つかった検索`FindNext`と次の出現箇所を検索します。

> [!CAUTION]
>  現在のレコードを編集する場合に呼び出すことによって、変更を保存することを確認して、`Update`別のレコードに移動する前に、メンバー関数。 更新することがなく別のレコードに移動すると、変更内容は警告なしに失われます。

検索操作のいずれかを使用ない呼び出しと同じ`MoveFirst`または`MoveNext`、ただし、これだけです、最初または次のレコード現在しなくても、条件を指定します。 移動操作で検索操作に従うことができます。

検索操作を使用する場合は、次に留意してください。

- 場合`Find`返します 0 以外の場合、現在のレコードが定義されていません。 この場合は、有効なレコードには、現在のレコード ポインターを配置する必要があります。

- 検索操作は、順方向専用スクロール スナップショットの種類のレコードを使用できません。

- 米国の日付形式 (1 か月-日-年) を使用する必要があります Microsoft Jet データベース エンジンの米国版を使用していない場合でも、日付を含むフィールドを検索するときそれ以外の場合、一致するレコードが見つからない可能性があります。

- ODBC データベースで大きなダイナセットを使用する場合は、検索操作が遅いこと、大きなレコード セットを使用する場合に特に検出可能性があります。 SQL クエリを使用してパフォーマンスを向上させることができますとカスタマイズ**ORDERBY**または**WHERE**句、パラメーター クエリ、または`CDaoQuerydef`インデックス付きの特定のレコードを取得するオブジェクト。

関連情報についてを参照してください"FindFirst、FindLast、FindNext、FindPrevious メソッド"DAO のヘルプします。

##  <a name="getabsoluteposition"></a>  CDaoRecordset::GetAbsolutePosition

レコード セット オブジェクトの現在のレコードのレコード数を返します。

```
long GetAbsolutePosition();
```

### <a name="return-value"></a>戻り値

レコード セットのレコードの数を 0 から整数。 レコード セット内の現在のレコードの序数位置に対応します。

### <a name="remarks"></a>Remarks

基になる DAO オブジェクトの AbsolutePosition プロパティの値が 0 から始まります。0 の設定は、レコード セットの最初のレコードを表します。 呼び出すことによって、レコード セット内のデータが設定されたレコードの数を判断する[GetRecordCount](#getrecordcount)します。 呼び出す`GetRecordCount`数を確認して、すべてのレコードにアクセスする必要がありますので、時間がかかる場合があります。

場合は、現在のレコードとして、レコード セット内のレコードがない場合 - 1 が返されます。 現在のレコードが削除された場合、AbsolutePosition プロパティの値が定義されていないと、MFC は、参照されている場合に例外をスローします。 ダイナセット タイプのレコード セットは、新しいレコードは、シーケンスの末尾に追加されます。

> [!NOTE]
>  このプロパティは、レコード番号の代わりとして使用するものではありません。 ブックマークが保持して、指定した位置に戻るをお勧めであり、あらゆる種類のレコード セット オブジェクトの現在のレコードを配置する唯一の方法です。 具体的には、前のレコードが削除されたときに特定のレコードの位置を変更します。 また、レコード セットを再作成を使用して SQL ステートメントで作成されたレコード セット内の各レコードの順序が保証されないため場合、特定のレコードが同じ絶対位置を持つことの保証はありません、 **ORDERBY**句。

> [!NOTE]
>  このメンバー関数がダイナセット タイプとスナップショットの種類のレコード セットに対してのみ有効です。

関連情報については、「AbsolutePosition プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getbookmark"></a>  CDaoRecordset::GetBookmark

特定のレコードのブックマークの値を取得するには、このメンバー関数を呼び出します。

```
COleVariant GetBookmark();
```

### <a name="return-value"></a>戻り値

現在のレコードのブックマークを表す値を返します。

### <a name="remarks"></a>Remarks

レコード セット オブジェクトを作成または開くときに各レコードは既に一意のブックマーク サポートしている場合。 呼び出す`CanBookmark`をレコード セットでブックマークをサポートするかどうかを判断します。

現在のレコードのブックマークを保存するには、ブックマークの値を割り当てることで、`COleVariant`オブジェクト。 別のレコードに移動した後、いつでもそのレコードにすばやく戻るを呼び出す`SetBookmark`の値に対応するパラメーターを持つ`COleVariant`オブジェクト。

> [!NOTE]
>  呼び出す[Requery](#requery) DAO のブックマークを変更します。

関連情報については、「Bookmark プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getcachesize"></a>  CDaoRecordset::GetCacheSize

キャッシュされたレコードの数を取得するには、このメンバー関数を呼び出します。

```
long GetCacheSize();
```

### <a name="return-value"></a>戻り値

ODBC データ ソースからローカルにキャッシュされたデータを含むダイナセット タイプのレコード セット内のレコードの数を示す値。

### <a name="remarks"></a>Remarks

データ キャッシュでは、ダイナセット タイプのレコード セット オブジェクトを使用してリモート サーバーからデータを取得するアプリケーションのパフォーマンスが向上します。 キャッシュは、サーバーから、アプリケーションの実行中にデータをもう一度要求は、最も最近取得されたデータを保持するローカル メモリ内のスペースです。 データが要求されると、Microsoft Jet データベース エンジンまず要求されたデータのキャッシュ時間がかかると、サーバーから取得するのではなく。 ODBC データ ソースから発生しないデータがキャッシュに保存されません。

アタッチのテーブルなど、任意の ODBC データ ソースには、ローカル キャッシュを持つことができます。

関連情報については、DAO のヘルプ トピック"CacheSize CacheStart プロパティ"を参照してください。

##  <a name="getcachestart"></a>  CDaoRecordset::GetCacheStart

最初のレコードをキャッシュするレコード セット内のブックマークの値を取得するには、このメンバー関数を呼び出します。

```
COleVariant GetCacheStart();
```

### <a name="return-value"></a>戻り値

A`COleVariant`キャッシュするレコード セットの最初のレコードのブックマークを指定します。

### <a name="remarks"></a>Remarks

Microsoft Jet データベース エンジンが、キャッシュからキャッシュの範囲内のレコードを要求し、サーバーからのキャッシュの範囲外のレコードを要求します。

> [!NOTE]
>  キャッシュから取得したレコードには、他のユーザーがデータ ソースに同時に行われた変更は反映されません。

関連情報については、DAO のヘルプ トピック"CacheSize CacheStart プロパティ"を参照してください。

##  <a name="getcurrentindex"></a>  CDaoRecordset::GetCurrentIndex

現在インデックス付きのテーブル型で使用されているインデックスを確認するには、このメンバー関数を呼び出す`CDaoRecordset`オブジェクト。

```
CString GetCurrentIndex();
```

### <a name="return-value"></a>戻り値

A`CString`現在テーブル型のレコード セットで使用されているインデックスの名前を格納しています。 インデックスが設定されていない場合は、空の文字列を返します。

### <a name="remarks"></a>Remarks

このインデックスは、テーブル型のレコード セット内のレコードの順序の基礎でありで使用されます、[シーク](#seek)レコードを検索するメンバー関数。

A`CDaoRecordset`オブジェクトは 1 つ以上のインデックスを持つことができますが、一度に 1 つのみのインデックスを使用することができます (ですが、 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)オブジェクトで定義されているいくつかのインデックスがあります)。

関連情報については、トピック「インデックス オブジェクト」および DAO のヘルプでは、"現在のインデックス"の定義を参照してください。

##  <a name="getdatecreated"></a>  CDaoRecordset::GetDateCreated

ベース テーブルが作成された日時を取得するには、このメンバー関数を呼び出します。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>戻り値

A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)基底のテーブルが作成された日時を含むオブジェクト。

### <a name="remarks"></a>Remarks

日付と時刻の設定は、ベース テーブルが作成されたコンピューターから派生します。

関連情報については、DAO のヘルプ トピックの"DateCreated、LastUpdated プロパティ"を参照してください。

##  <a name="getdatelastupdated"></a>  CDaoRecordset::GetDateLastUpdated

スキーマの最終更新日時を取得するには、このメンバー関数を呼び出します。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>戻り値

A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)ベース テーブルの構造 (スキーマ) が最後に更新された日時を含むオブジェクト。

### <a name="remarks"></a>Remarks

日付と時刻の設定は、ベース テーブルの構造 (スキーマ) が最後に更新されたコンピューターから派生します。

関連情報については、DAO のヘルプ トピックの"DateCreated、LastUpdated プロパティ"を参照してください。

##  <a name="getdefaultdbname"></a>  CDaoRecordset::GetDefaultDBName

このレコード セットに対して、データベースの名前を確認するには、このメンバー関数を呼び出します。

```
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>戻り値

A`CString`このレコード セットの派生元のデータベースの名前とパスを格納しています。

### <a name="remarks"></a>Remarks

ポインターを指定せず、レコード セットを作成した場合、 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)既定のデータベースを開けませんこのパスがレコード セットが使用されます。 既定では、この関数は、空の文字列を返します。 ClassWizard がから新しいレコード セットを派生するときに`CDaoRecordset`、この関数が作成されます。

次の例は、二重の円記号の使用を示します (\\\\)、文字列では、文字列を正しく解釈されるように必須です。

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

##  <a name="getdefaultsql"></a>  CDaoRecordset::GetDefaultSQL

フレームワークは、レコード セットの基になる既定の SQL ステートメントを取得するには、このメンバー関数を呼び出します。

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>戻り値

A`CString`既定の SQL ステートメントを格納しています。

### <a name="remarks"></a>Remarks

これは、テーブル名または SQL**選択**ステートメント。

直接定義する既定の SQL ステートメントで ClassWizard、レコード セット クラスを宣言することで、ClassWizard では、このタスクを実行できます。

Null SQL 文字列を渡した場合[オープン](#open)、レコード セットをテーブル名または SQL を決める際にこの関数が呼び出されます。

##  <a name="geteditmode"></a>  CDaoRecordset::GetEditMode

これは、次の値のいずれかのこのメンバー関数の編集、状態を確認するを呼び出します。

```
short GetEditMode();
```

### <a name="return-value"></a>戻り値

現在のレコードの編集状態を示す値を返します。

### <a name="remarks"></a>Remarks

|[値]|説明|
|-----------|-----------------|
|`dbEditNone`|編集操作が進行中ではありません。|
|`dbEditInProgress`|`Edit` 呼び出されました。|
|`dbEditAdd`|`AddNew` 呼び出されました。|

関連情報については、「EditMode プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getfieldcount"></a>  CDaoRecordset::GetFieldCount

レコード セットで定義されたフィールド (列) の数を取得するには、このメンバー関数を呼び出します。

```
short GetFieldCount();
```

### <a name="return-value"></a>戻り値

レコード セットのフィールドの数。

### <a name="remarks"></a>Remarks

関連情報については、「Count プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getfieldinfo"></a>  CDaoRecordset::GetFieldInfo

レコード セットのフィールドについての情報を取得するには、このメンバー関数を呼び出します。

```
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
インデックスで検索する場合、レコード セットのフィールド コレクションの定義済みフィールドの 0 から始まるインデックス。

*fieldinfo*<br/>
参照を[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)構造体。

*dwInfoOptions*<br/>
取得するレコード セットに関する情報を指定するオプション。 使用可能なオプションを返す関数がどのようなと共に挙げています。 最適なパフォーマンスを必要な情報のレベルのみを取得します。

- `AFX_DAO_PRIMARY_INFO` (既定値)名前、種類、サイズ、属性

- `AFX_DAO_SECONDARY_INFO` プライマリの情報と。必要に応じて、序数の位置、長さ 0 は、順序、外部名、ソース フィールド、ソース テーブルの照合を許可します。

- `AFX_DAO_ALL_INFO` プライマリとセカンダリの情報と。既定の値、検証規則、検証テキスト

*lpszName*<br/>
フィールドの名前。

### <a name="remarks"></a>Remarks

関数の 1 つのバージョンでは、インデックスを使用してフィールドを検索することができます。 その他のバージョンでは、フィールド名で検索できます。

返される情報については、次を参照してください。、 [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)構造体。 この構造体メンバーの説明に上記の情報の項目に対応するは*dwInfoOptions*します。 1 つのレベルの情報を要求するときに、そのレベルもの情報を取得します。

関連情報については、「属性のプロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getfieldvalue"></a>  CDaoRecordset::GetFieldValue

レコード セット内のデータを取得するには、このメンバー関数を呼び出します。

```
virtual void GetFieldValue(
    LPCTSTR lpszName,
    COleVariant& varValue);

virtual void GetFieldValue(
    int nIndex,
    COleVariant& varValue);

virtual COleVariant GetFieldValue(LPCTSTR lpszName);
virtual COleVariant GetFieldValue(int nIndex);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
フィールドの名前を含む文字列へのポインター。

*varValue*<br/>
参照を`COleVariant`フィールドの値を格納するオブジェクト。

*nIndex*<br/>
インデックスで検索する場合、レコード セットのフィールド コレクション内のフィールドの 0 から始まるインデックス。

### <a name="return-value"></a>戻り値

2 つのバージョンの`GetFieldValue`戻り値を返す、 [COleVariant](../../mfc/reference/colevariant-class.md)フィールドの値を格納しているオブジェクト。

### <a name="remarks"></a>Remarks

名前または序数位置では、フィールドを検索できます。

> [!NOTE]
>  呼び出しを受け取るこのメンバー関数のバージョンのいずれかに効率的です、`COleVariant`を返すバージョンの呼び出しではなく、パラメーターとしてオブジェクト参照を`COleVariant`オブジェクト。 この関数の以前のバージョンは、旧バージョンとの互換性のために保持されます。

使用`GetFieldValue`と[いる](#setfieldvalue)実行時ではなく静的を使用してバインド列にフィールドに動的にバインドする、 [DoFieldExchange](#dofieldexchange)メカニズム。

`GetFieldValue` および`DoFieldExchange`メカニズムは、パフォーマンスを向上させるために組み合わせることができます。 たとえば、使用して`GetFieldValue`をオンデマンドでのみ必要な値を取得し、インターフェイスの「詳細」ボタンには、その呼び出しを割り当てます。

関連情報については、「フィールド オブジェクト」と「値プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getindexcount"></a>  CDaoRecordset::GetIndexCount

テーブル型のレコード セットで使用できるインデックスの数を決定するには、このメンバー関数を呼び出します。

```
short GetIndexCount();
```

### <a name="return-value"></a>戻り値

テーブル型のレコード セット内のインデックスの数。

### <a name="remarks"></a>Remarks

`GetIndexCount` レコード セット内のすべてのインデックスをループに役立ちます。 そのために、使用`GetIndexCount`と共に[GetIndexInfo](#getindexinfo)します。 ダイナセットの種類またはスナップショットの種類のレコード セットでこのメンバー関数を呼び出すと、MFC は、例外をスローします。

関連情報については、「属性のプロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getindexinfo"></a>  CDaoRecordset::GetIndexInfo

さまざまな種類のレコード セットを基になるベース テーブルで定義されているインデックスの情報を取得するには、このメンバー関数を呼び出します。

```
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
数値の位置で検索する場合、テーブルのインデックスのコレクション内の 0 から始まるインデックス。

*indexinfo*<br/>
参照を[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)構造体。

*dwInfoOptions*<br/>
取得するインデックスに関する情報を指定するオプション。 使用可能なオプションを返す関数がどのようなと共に挙げています。 最適なパフォーマンスを必要な情報のレベルのみを取得します。

- `AFX_DAO_PRIMARY_INFO` (既定値)名前、フィールドについては、フィールド

- `AFX_DAO_SECONDARY_INFO` プライマリの情報と。プライマリで一意で、クラスター化 IgnoreNulls、必要に応じて、外部

- `AFX_DAO_ALL_INFO` プライマリとセカンダリの情報と。Distinct Count

*lpszName*<br/>
名前で検索する場合、インデックス オブジェクトの名前へのポインター。

### <a name="remarks"></a>Remarks

関数の 1 つのバージョンでは、コレクション内の位置でインデックスを検索することができます。 その他のバージョンでは、名前、インデックスを検索することができます。

返される情報については、次を参照してください。、 [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)構造体。 この構造体メンバーの説明に上記の情報の項目に対応するは*dwInfoOptions*します。 1 つのレベルの情報を要求するときに、そのレベルもの情報を取得します。

関連情報については、「属性のプロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getlastmodifiedbookmark"></a>  CDaoRecordset::GetLastModifiedBookmark

最も最近追加または更新されたレコードのブックマークを取得するには、このメンバー関数を呼び出します。

```
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>戻り値

A`COleVariant`最後を示すブックマークを含む、追加またはレコードを変更します。

### <a name="remarks"></a>Remarks

レコード セット オブジェクトを作成または開くときに各レコードは既に一意のブックマーク サポートしている場合。 呼び出す[GetBookmark](#getbookmark)をレコード セットにブックマークがサポートしているかを判断します。 レコード セットは、ブックマークをサポートしていない場合、`CDaoException`がスローされます。

レコードを追加するときに、レコード セットの最後に表示し、現在のレコードではありません。 新しいレコードを現在させるには、呼び出す`GetLastModifiedBookmark`を呼び出して`SetBookmark`を新しく追加したレコードを返します。

関連情報については、「LastModified プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getlockingmode"></a>  CDaoRecordset::GetLockingMode

レコード セットの有効なロックの種類を決定するには、このメンバー関数を呼び出します。

```
BOOL GetLockingMode();
```

### <a name="return-value"></a>戻り値

以外の場合、ロックの種類は、ペシミスティック ロックの場合は 0。

### <a name="remarks"></a>Remarks

呼び出すとすぐにロックされているときに排他ロックが実際には、データ ページを編集しているレコードを含む、[編集](#edit)メンバー関数。 呼び出すと、ページはロックが、 [Update](#update)または[閉じる](#close)メンバー関数、または、移動または検索操作のいずれか。

レコードの更新中にのみレコードを含むデータ ページがロックされているときに、オプティミスティック ロックが有効になって、`Update`メンバー関数。

ODBC データ ソースを使用する場合のロック モードはオプティミスティックは常にします。

関連情報については、「LockEdits プロパティ」と「ロックの動作でマルチ ユーザー アプリケーション」DAO ヘルプのトピックを参照してください。

##  <a name="getname"></a>  CDaoRecordset::GetName

レコード セットの名前を取得するには、このメンバー関数を呼び出します。

```
CString GetName();
```

### <a name="return-value"></a>戻り値

A`CString`レコード セットの名前を格納します。

### <a name="remarks"></a>Remarks

レコード セットの名前は文字で始める必要があり、最大 40 文字を含めることができます。 数字を含めることができ、アンダー スコア文字しますが、区切り記号やスペースを含めることはできません。

関連情報については、「Name プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getparamvalue"></a>  CDaoRecordset::GetParamValue

基になる DAOParameter オブジェクトに格納されている指定されたパラメーターの現在の値を取得するには、このメンバー関数を呼び出します。

```
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
基になる DAOParameter オブジェクトで、パラメーターの数値の位置。

*lpszName*<br/>
値を取得するパラメーターの名前。

### <a name="return-value"></a>戻り値

クラスのオブジェクト[COleVariant](../../mfc/reference/colevariant-class.md)パラメーターの値を格納しています。

### <a name="remarks"></a>Remarks

名前またはコレクション内の位置のいずれかのパラメーターを表示できます。

関連情報については、「パラメーター オブジェクト」DAO ヘルプのトピックを参照してください。

##  <a name="getpercentposition"></a>  CDaoRecordset::GetPercentPosition

呼び出すダイナセット タイプまたはスナップショットの種類のレコード セットを使用しているときに`GetPercentPosition`の移動量が呼び出すことによって示されるアクセスできるレコードの数を基準としたが、レコード セットを完全に設定するには、する前に[GetRecordCount](#getrecordcount).

```
float GetPercentPosition();
```

### <a name="return-value"></a>戻り値

0 ~ 100 の数値では、レコード セット内のレコードに対する割合に基づいて、レコード セット オブジェクトの現在のレコードのおおよその場所を示します。

### <a name="remarks"></a>Remarks

移動できます最後のレコードを呼び出して[MoveLast](#movelast)に完全なすべてのレコード セットが、これの母集団かかる場合がありますかなりの時間。

呼び出すことができます`GetPercentPosition`ですべての 3 種類のレコード セット オブジェクトで行うために、インデックスなしテーブルを含むです。 ただし、呼び出すことはできません`GetPercentPosition`スクロール順方向専用のスナップショット、または外部のデータベースに対してパススルー クエリから開かれたレコード セット。 現在のレコードがないか、彼は現在のレコードが削除された場合、`CDaoException`がスローされます。

関連情報については、「PercentPosition プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getrecordcount"></a>  CDaoRecordset::GetRecordCount

レコード セットのレコードの数がアクセスを確認するには、このメンバー関数を呼び出します。

```
long GetRecordCount();
```

### <a name="return-value"></a>戻り値

レコード セット オブジェクトにアクセスするレコードの数を返します。

### <a name="remarks"></a>Remarks

`GetRecordCount` すべてのレコードがアクセスされるまでダイナセット型、またはスナップショットの種類のレコード セットに含まれるレコードの数は示しません。 このメンバー関数の呼び出しでは、かなりの所要時間をかかる場合があります。

最後のレコードにアクセスすると、戻り値は、レコード セットの削除の取り消しレコードの合計数を示します。 最後のレコードにアクセスを強制的に、`MoveLast`または`FindLast`レコード セットのメンバー関数。 クエリが返すレコードのおおよその数を決定するのに SQL の数を使用することもできます。

ダイナセット タイプのレコード セットでの戻り値のレコードの削除、アプリケーションと`GetRecordCount`が減少します。 ただし、他のユーザーによって削除されたレコードはで反映されません`GetRecordCount`まで、現在のレコードが削除されたレコードに配置されています。 レコードの数に影響を与えるトランザクションを実行し、その後、トランザクションをロールバックして`GetRecordCount`は実際の残りのレコード数が反映されません。

値`GetRecordCount`スナップショットの種類のレコード セットからは、基になるテーブルの変更内容によっては影響ありませんが。

値`GetRecordCount`テーブル型からレコード セットがテーブル内のレコードのおおよその数を反映し、テーブルのレコードの追加し、削除、すぐに影響を受けますが。

レコードとレコード セットは、0 の値を返します。 接続されているテーブルまたは ODBC のデータベースを扱うとき`GetRecordCount`常に - 1 を返します。 呼び出す、`Requery`のレコード セットのメンバー関数の値にリセット`GetRecordCount`クエリが再実行された場合と同様です。

関連情報については、「RecordCount プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getsql"></a>  CDaoRecordset::GetSQL

このメンバー関数 get が開かれたときに、レコード セットのレコードを選択するために使用された SQL ステートメントを呼び出します。

```
CString GetSQL() const;
```

### <a name="return-value"></a>戻り値

A `CString` SQL ステートメントを格納しています。

### <a name="remarks"></a>Remarks

SQL はこれが、一般に**選択**ステートメント。

によって返される文字列`GetSQL`通常とは異なる任意の文字列でレコード セットに渡した場合がありますが、 *lpszSQL*パラメーターを[オープン](#open)メンバー関数。 これは、レコード セットに渡される内容に基づく完全な SQL ステートメントを作成するため`Open`、ClassWizard で指定したものとする可能性があります指定したもので、[か](#m_strfilter)と[レコード](#m_strsort)データ メンバー。

> [!NOTE]
>  このメンバー関数を呼び出した後にのみ呼び出す`Open`します。

関連情報については、DAO ヘルプの「SQL プロパティ」を参照してください。

##  <a name="gettype"></a>  CDaoRecordset::GetType

レコード セット オブジェクトの種類を決定するレコード セットを開いた後に、このメンバー関数を呼び出します。

```
short GetType();
```

### <a name="return-value"></a>戻り値

レコード セットの種類を示す値は次のいずれか:

- `dbOpenTable` テーブル型のレコード セット

- `dbOpenDynaset` ダイナセット タイプのレコード セット

- `dbOpenSnapshot` スナップショットの種類のレコード セット

### <a name="remarks"></a>Remarks

関連情報については、「型のプロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getvalidationrule"></a>  CDaoRecordset::GetValidationRule

データの検証に使用されるルールを確認するには、このメンバー関数を呼び出します。

```
CString GetValidationRule();
```

### <a name="return-value"></a>戻り値

A`CString`が変更またはテーブルに追加すると、レコード内のデータを検証する値を含むオブジェクト。

### <a name="remarks"></a>Remarks

このルールは、テキスト ベース、基になるテーブルが変更されるたびに適用されます。 データが有効でない場合、MFC は、例外をスローします。 返されたエラー メッセージは、指定した場合は基になるフィールド オブジェクトのプロパティのテキストまたは基になるフィールド オブジェクトのプロパティで指定された式のテキストです。 呼び出すことができます[GetValidationText](#getvalidationtext)エラー メッセージのテキストを取得します。

たとえば、月の日を必要とするレコードのフィールドがあります検証規則をなど"日 BETWEEN 1 から 31 です"。

関連情報については、"Validationrule"DAO ヘルプのトピックを参照してください。

##  <a name="getvalidationtext"></a>  CDaoRecordset::GetValidationText

基になるフィールド オブジェクトのプロパティのテキストを取得するには、このメンバー関数を呼び出します。

```
CString GetValidationText();
```

### <a name="return-value"></a>戻り値

A`CString`フィールドの値が基になるフィールド オブジェクトの検証規則を満たしていない場合に表示されるメッセージのテキストを含むオブジェクト。

### <a name="remarks"></a>Remarks

関連情報については、「プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="isbof"></a>  CDaoRecordset::IsBOF

レコードからレコードについては、レコード セットの最初のレコードの前に位置しているかどうかにスクロールする前に、このメンバー関数を呼び出します。

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>戻り値

レコード セットにレコードが含まれていない場合、または最初のレコードの前にスクロールした場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

呼び出すこともできます`IsBOF`と共に`IsEOF`をレコード セットにレコードがかが空かどうかを判断します。 呼び出した後にすぐに`Open`、レコード セットにレコードが含まれていない場合は、 `IsBOF` 0 以外の値を返します。 少なくとも 1 つのレコードがレコード セットを開くと、最初のレコードは、現在のレコードと`IsBOF`0 を返します。

最初のレコードが現在のレコードを呼び出す場合`MovePrev`、`IsBOF`後以外を返します。 場合`IsBOF`呼び出す 0 以外を返しますと`MovePrev`例外がスローされます。 場合`IsBOF`戻り値は 0 以外の場合、現在のレコードが定義されていないと、現在のレコードを必要とする任意のアクション、例外が発生します。

特定のメソッドの効果`IsBOF`と`IsEOF`設定。

- 呼び出す`Open*`内部的には、最初のレコード、レコード セットの現在のレコードを呼び出して`MoveFirst`します。 そのため、`Open`レコード原因の空のセットで`IsBOF`と`IsEOF`を 0 以外の値を返します。 (失敗したときの動作については、次の表を参照してください`MoveFirst`または`MoveLast`呼び出し。)。

- レコードを正常に配置したすべての移動操作が両方とも`IsBOF`と`IsEOF`0 を返します。

- `AddNew`呼び出し後に、`Update`呼び出しが正常に新しいレコードを挿入すると、`IsBOF`を返す場合にのみが 0、`IsEOF`が既に 0 以外。 状態`IsEOF`は常に変更されません。 Microsoft Jet データベース エンジンによって定義されたは、現在のレコードの後、新しいレコードが挿入されるため、空のレコード セットの現在のレコード ポインターは、ファイルの最後にします。

- すべて`Delete`呼び出し、残っている唯一のレコードをレコード セットから削除する場合でも、値は変更の`IsBOF`または`IsEOF`します。

この表では、さまざまな組み合わせで許可されている移動操作`IsBOF` / `IsEOF`します。

||MoveFirst、MoveLast|MovePrev、<br /><br /> < 0 を移動します。|0 を移動します。|MoveNext、<br /><br /> > 0 を移動します。|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= 0 以外の場合、<br /><br /> `IsEOF`=0|Allowed|例外|例外|Allowed|
|`IsBOF`=0,<br /><br /> `IsEOF`=nonzero|Allowed|Allowed|例外|例外|
|どちらも 0 以外の場合|例外|例外|例外|例外|
|どちらも 0|Allowed|Allowed|Allowed|Allowed|

移動操作を許可してもの操作が正常にレコードを見つけるとは限りません。 指定された移動操作を実行しようとすると、は許可され、例外が発生しないだけを示します。 値、`IsBOF`と`IsEOF`メンバー関数を実行しようとした移行の結果として変更可能性があります。

値には、レコードを特定する移動操作の効果`IsBOF`と`IsEOF`設定が次の表に示すようにします。

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|0 以外の場合|0 以外の場合|
|`Move` 0|変更なし|変更なし|
|`MovePrev`, `Move` < 0|0 以外の場合|変更なし|
|`MoveNext`, `Move` > 0|変更なし|0 以外の場合|

関連情報については、トピックを参照してください。"BOF、EOF プロパティ"DAO のヘルプ。

##  <a name="isdeleted"></a>  CDaoRecordset::IsDeleted

現在のレコードが削除されたかどうかを判断するには、このメンバー関数を呼び出します。

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>戻り値

レコード セットが削除済みのレコードに配置されている場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

レコードをスクロールする場合と`IsDeleted`TRUE (0 以外) が返されますし、その他のレコード セットの操作を実行する前に、別のレコードをスクロールする必要があります。

> [!NOTE]
>  スナップショット パブリケーションまたはテーブル型のレコード セット内のレコードの削除された状態を確認する必要はありません。 呼び出す必要はありません、スナップショットからレコードを削除できません、ため`IsDeleted`します。 テーブル型のレコード セットの削除されたレコードはレコード セットから実際に削除します。 レコードが削除されたして別のユーザーまたは別のレコード セット内のいずれかと、そのレコードにスクロールすることはできません。 そのためを呼び出す必要はありません`IsDeleted`します。

ダイナセットからレコードを削除すると、レコード セットから削除され、そのレコードにスクロールすることはできません。 ただし場合内のレコード ダイナセットは削除別のユーザーによってまたは別のレコード セットが、同じテーブルに基づく`IsDeleted`は後でそのレコードをスクロールすると TRUE を返します。

関連情報については、「メソッドの削除」、「LastModified プロパティ」と「EditMode プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="iseof"></a>  CDaoRecordset::IsEOF

レコードからレコードについては、レコード セットの最後のレコードを越えているかどうかにスクロールするには、このメンバー関数を呼び出します。

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>戻り値

レコード セットにレコードが含まれていない場合、または最後のレコードより後にスクロールする場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

呼び出すこともできます`IsEOF`をレコード セットにレコードがかが空かどうかを判断します。 呼び出した後にすぐに`Open`、レコード セットにレコードが含まれていない場合は、 `IsEOF` 0 以外の値を返します。 少なくとも 1 つのレコードがレコード セットを開くと、最初のレコードは、現在のレコードと`IsEOF`0 を返します。

呼び出すときに、最後のレコードが現在のレコードがかどうか`MoveNext`、`IsEOF`後以外を返します。 場合`IsEOF`呼び出す 0 以外を返しますと`MoveNext`例外がスローされます。 場合`IsEOF`戻り値は 0 以外の場合、現在のレコードが定義されていないと、現在のレコードを必要とする任意のアクション、例外が発生します。

特定のメソッドの効果`IsBOF`と`IsEOF`設定。

- 呼び出す`Open`内部的には、最初のレコード、レコード セットの現在のレコードを呼び出して`MoveFirst`します。 そのため、`Open`レコード原因の空のセットで`IsBOF`と`IsEOF`を 0 以外の値を返します。 (失敗したときの動作については、次の表を参照してください`MoveFirst`呼び出し。)。

- レコードを正常に配置したすべての移動操作が両方とも`IsBOF`と`IsEOF`0 を返します。

- `AddNew`呼び出し後に、`Update`呼び出しが正常に新しいレコードを挿入すると、`IsBOF`を返す場合にのみが 0、`IsEOF`が既に 0 以外。 状態`IsEOF`は常に変更されません。 Microsoft Jet データベース エンジンによって定義されたは、現在のレコードの後、新しいレコードが挿入されるため、空のレコード セットの現在のレコード ポインターは、ファイルの最後にします。

- すべて`Delete`呼び出し、残っている唯一のレコードをレコード セットから削除する場合でも、値は変更の`IsBOF`または`IsEOF`します。

この表では、さまざまな組み合わせで許可されている移動操作`IsBOF` / `IsEOF`します。

||MoveFirst、MoveLast|MovePrev、<br /><br /> < 0 を移動します。|0 を移動します。|MoveNext、<br /><br /> > 0 を移動します。|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= 0 以外の場合、<br /><br /> `IsEOF`=0|Allowed|例外|例外|Allowed|
|`IsBOF`=0,<br /><br /> `IsEOF`=nonzero|Allowed|Allowed|例外|例外|
|どちらも 0 以外の場合|例外|例外|例外|例外|
|どちらも 0|Allowed|Allowed|Allowed|Allowed|

移動操作を許可してもの操作が正常にレコードを見つけるとは限りません。 指定された移動操作を実行しようとすると、は許可され、例外が発生しないだけを示します。 値、`IsBOF`と`IsEOF`メンバー関数を実行しようとした移行の結果として変更可能性があります。

値には、レコードを特定する移動操作の効果`IsBOF`と`IsEOF`設定が次の表に示すようにします。

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|0 以外の場合|0 以外の場合|
|`Move` 0|変更なし|変更なし|
|`MovePrev`, `Move` < 0|0 以外の場合|変更なし|
|`MoveNext`, `Move` > 0|変更なし|0 以外の場合|

関連情報については、トピックを参照してください。"BOF、EOF プロパティ"DAO のヘルプ。

##  <a name="isfielddirty"></a>  CDaoRecordset::IsFieldDirty

このメンバー関数は「ダーティ」としてダイナセットの指定したフィールドのデータ メンバーのフラグが設定されているかどうかを判断する (変更) を呼び出します。

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>パラメーター

*現在価値*<br/>
チェック、またはフィールドのいずれがダーティかどうかを判断する場合は NULL を状態フィールド データ メンバーへのポインター。

### <a name="return-value"></a>戻り値

指定したフィールドのデータ メンバーがダーティ; としてフラグが設定された場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

すべてのダーティ フィールド データ メンバー内のデータ転送されます、レコードをデータ ソースへの呼び出しによって、現在のレコードが更新されたときに、`Update`のメンバー関数`CDaoRecordset`(の呼び出しに続く`Edit`または`AddNew`)。 この知識があれば、さらに手順を実行できますなどに対するデータ ソースに書き込まれませんので、列をマークするフィールドのデータ メンバー。

`IsFieldDirty` によって実装`DoFieldExchange`します。

##  <a name="isfieldnull"></a>  CDaoRecordset::IsFieldNull

レコード セットの指定したフィールドのデータ メンバーを Null としてマークされているかどうかを判断するには、このメンバー関数を呼び出します。

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>パラメーター

*現在価値*<br/>
チェック、またはフィールドのいずれかが Null であるかどうかを判断する場合は NULL を状態フィールド データ メンバーへのポインター。

### <a name="return-value"></a>戻り値

指定したフィールドのデータ メンバーが Null としてフラグが設定された場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

(データベース用語では、Null「値を持たない」手段と C++ では NULL の場合と同じではありません)。フィールド データ メンバーが Null としてフラグが設定した場合は、対象の値がない現在のレコードの列として解釈されます。

> [!NOTE]
>  使用して、特定の状況で`IsFieldNull`できる効率的な場合は、次のコード例に示すようにします。

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
>  派生することがなく、レコードの動的バインドを使用しているかどうかは`CDaoRecordset`、の例で示す VT_ を使用してください。

##  <a name="isfieldnullable"></a>  CDaoRecordset::IsFieldNullable

指定したフィールドのデータ メンバーは"null 値を許容"するかどうかを判断する (できますに設定する、Null 値です。 このメンバー関数を呼び出すC++ の NULL でないと null の場合、つまり、データベース用語では、同じ「値を持たない」)。

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>パラメーター

*現在価値*<br/>
チェック、またはフィールドのいずれかが Null であるかどうかを判断する場合は NULL を状態フィールド データ メンバーへのポインター。

### <a name="return-value"></a>戻り値

指定したフィールドのデータ メンバーが Null です。 ができる場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

Null 値はフィールド値が必要です。 このようなフィールドを追加またはレコードを更新する場合は Null に設定しようとすると、データ ソースは追加や更新を拒否し、`Update`例外がスローされます。 呼び出すときに、例外が発生した`Update`を呼び出すときではなく、`SetFieldNull`します。

##  <a name="isopen"></a>  CDaoRecordset::IsOpen

レコード セットが開いているかどうかを判断するには、このメンバー関数を呼び出します。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>戻り値

0 以外の値、レコード セット オブジェクトの`Open`または`Requery`メンバー関数が呼び出された以前とレコード セットが終了されていない。 それ以外の場合に 0 です。

### <a name="remarks"></a>Remarks

##  <a name="m_bcheckcachefordirtyfields"></a>  CDaoRecordset::m_bCheckCacheForDirtyFields

かどうかキャッシュされているフィールドに自動的にマークがダーティ (変更) を示すフラグを格納し、Null。

### <a name="remarks"></a>Remarks

フラグの既定値は TRUE。 このデータ メンバーの設定では、全体のダブル バッファリング機構を制御します。 フラグを TRUE に設定する場合は、DFX のメカニズムを使用してフィールドの単位でキャッシュを無効にできます。 呼び出す必要がある場合は、フラグを FALSE に設定すると、`SetFieldDirty`と`SetFieldNull`自分でします。

呼び出しの前にこのデータ メンバーを設定`Open`します。 このメカニズムでは、使いやすさを主にします。 パフォーマンスは、変更が加えられると、フィールドのダブル バッファリングにより遅いことがあります。

##  <a name="m_nfields"></a>  CDaoRecordset::m_nFields

レコード セット クラスのフィールド データ メンバーの数と、データ ソースからレコード セットが選択した列の数が含まれています。

### <a name="remarks"></a>Remarks

レコード セット クラスのコンス トラクターを初期化する必要があります`m_nFields`と静的にバインドされたフィールドの正しい数。 ClassWizard は、レコード セット クラスを宣言に使用するときに、この初期化を書き込みます。 手動で記述することもできます。

フレームワークでは、この番号を使用して、フィールド データ メンバーと、データ ソースの現在のレコードの対応する列の間の相互作用を管理します。

> [!NOTE]
>  この番号に登録されている出力列の数に対応する必要があります`DoFieldExchange`呼び出しの後に`SetFieldType`パラメーターと共に`CDaoFieldExchange::outputColumn`します。

動作を動的に列をバインドする`CDaoRecordset::GetFieldValue`と`CDaoRecordset::SetFieldValue`します。 これを行う場合は カウントをインクリメントする必要はありません`m_nFields`呼び出し DFX 関数の数を反映するように、`DoFieldExchange`メンバー関数。

##  <a name="m_nparams"></a>  CDaoRecordset::m_nParams

レコード セット クラスでパラメーターのデータ メンバーの数が含まれています — レコード セットのクエリで渡されるパラメーターの数。

### <a name="remarks"></a>Remarks

クラスのコンス トラクターを初期化する必要があります、レコード セット クラスにパラメーター データ メンバーがある場合は、 *m_nParams*正しい番号。 値*m_nParams*既定値は 0。 パラメーターのデータ メンバーを追加する場合、手動で行うことができます: パラメーターの数を反映するようにクラスのコンス トラクターで初期化を手動で追加する必要があります (の数とサイズ以上である必要がありますが ' 内のプレース ホルダー、*か*または*レコード*文字列)。

フレームワークは、レコード セットのクエリをパラメーター化するときに、この番号を使用します。

> [!NOTE]
>  この番号は、"params"に登録されている数に対応する必要があります`DoFieldExchange`呼び出しの後に`SetFieldType`パラメーターと共に`CFieldExchange::param`します。

関連情報については、「パラメーター オブジェクト」DAO ヘルプのトピックを参照してください。

##  <a name="m_pdaorecordset"></a>  CDaoRecordset::m_pDAORecordset

基に DAO レコード セット オブジェクトの OLE インターフェイスへのポインターが含まれています、`CDaoRecordset`オブジェクト。

### <a name="remarks"></a>Remarks

DAO インターフェイスに直接アクセスする必要がある場合は、このポインターを使用します。

関連情報については、「レコード セット オブジェクト」DAO のヘルプ トピックを参照してください。

##  <a name="m_pdatabase"></a>  CDaoRecordset::m_pDatabase

ポインターが含まれています、`CDaoDatabase`オブジェクトにより、レコード セットはデータ ソースに接続します。

### <a name="remarks"></a>Remarks

この変数は、2 つの方法で設定されます。 通常、既に開いているにポインターを渡す`CDaoDatabase`recordset オブジェクトを構築するときのオブジェクトします。 代わりに、NULL を渡す場合`CDaoRecordset`作成、`CDaoDatabase`オブジェクトされ開かれます。 いずれの場合も、`CDaoRecordset`この変数にマウス ポインターを格納します。

通常は直接不要に格納されているポインターを使用する`m_pDatabase`します。 独自の拡張機能を記述する場合`CDaoRecordset`、ただし、ポインターを使用して必要な場合があります。 たとえば、する必要があります、ポインターをスローする場合、独自`CDaoException`(秒)。

関連情報については、「データベースのオブジェクト」DAO ヘルプのトピックを参照してください。

##  <a name="m_strfilter"></a>  CDaoRecordset::m_strFilter

構築するために使用する文字列を含む、**WHERE**SQL ステートメントの句。

### <a name="remarks"></a>Remarks

予約語を含まない**WHERE**をレコード セットをフィルター処理します。 このデータ メンバーの使用では、テーブル型のレコード セットに適用されません。 使用`m_strFilter`を使用して、レコード セットを開くときに影響を与えませんを`CDaoQueryDef`ポインター。

米国の日付形式 (1 か月-日-年) を使用して、Microsoft Jet データベース エンジンの米国版を使用していない場合でも、日付を含むフィールドをフィルター処理する場合それ以外の場合、データがフィルター処理されません想像のとおりです。

関連情報については、「フィルター プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="m_strsort"></a>  CDaoRecordset::m_strSort

格納する文字列が含まれています、 **ORDERBY**予約語を含まない SQL ステートメントの句**ORDERBY**します。

### <a name="remarks"></a>Remarks

ダイナセット、スナップショットの種類のレコード セット オブジェクトを並べ替えることができます。

テーブル型のレコード セット オブジェクトを並べ替えることはできません。 テーブル型のレコード セットの並べ替え順序を確認するのには、呼び出す[SetCurrentIndex](#setcurrentindex)します。

使用*レコード*を使用して、レコード セットを開くときに影響を与えませんを`CDaoQueryDef`ポインター。

関連情報については、「並べ替えのプロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="move"></a>  CDaoRecordset::Move

レコード セットに移動するには、このメンバー関数を呼び出す*lRows*現在のレコードからのレコード。

```
virtual void Move(long lRows);
```

### <a name="parameters"></a>パラメーター

*lRows*<br/>
前方または後方に移動するレコードの数。 正の値は、レコード セットの末尾方向へ転送、移動します。 負の値は、先頭に向かって後方移動します。

### <a name="remarks"></a>Remarks

前方または後方に移動することができます。 `Move( 1 )` 等価`MoveNext`、および`Move( -1 )`と等価`MovePrev`します。

> [!CAUTION]
>  いずれかを呼び出し、`Move`レコード セットにレコードが存在しない場合、関数が例外をスローします。 一般に、両方を呼び出す`IsBOF`と`IsEOF`移動操作を任意のレコードをレコード セットが存在するかどうかを判断する前にします。 呼び出した後`Open`または`Requery`、いずれかを呼び出す`IsBOF`または`IsEOF`します。

> [!NOTE]
>  先頭またはレコード セットの末尾を越えてスクロールした場合 (`IsBOF`または`IsEOF`0 以外の値を返します) への呼び出し`Move`スロー、`CDaoException`します。

> [!NOTE]
>  呼び出す場合、`Move`関数の現在のレコードがされている間に更新または追加、更新は警告なしに破棄します。

呼び出すと`Move`方向スクロールのスナップショットで、 *lRows*パラメーターは正の整数である必要があります、ため、先に進めるだけ、ブックマークは使用できません。

最初、最後に、次に、前レコードまたはレコード セットの現在のレコードを呼び出し、 `MoveFirst`、 `MoveLast`、 `MoveNext`、または`MovePrev`メンバー関数。

関連情報については、「メソッドの移動」トピックを参照してください。"MoveFirst、MoveLast、MoveNext、MovePrevious メソッド"と DAO のヘルプ。

##  <a name="movefirst"></a>  CDaoRecordset::MoveFirst

(ある場合)、レコード セットの最初のレコードを作成するには、このメンバー関数を呼び出して、現在のレコード。

```
void MoveFirst();
```

### <a name="remarks"></a>Remarks

呼び出す必要はありません`MoveFirst`レコード セットを開いた直後後。 その時点では、(ある場合) は、最初のレコードは、現在のレコードでは自動的にします。

> [!CAUTION]
>  いずれかを呼び出し、`Move`レコード セットにレコードが存在しない場合、関数が例外をスローします。 一般に、両方を呼び出す`IsBOF`と`IsEOF`移動操作を任意のレコードをレコード セットが存在するかどうかを判断する前にします。 呼び出した後`Open`または`Requery`、いずれかを呼び出す`IsBOF`または`IsEOF`します。

> [!NOTE]
>  呼び出す場合、`Move`関数の現在のレコードがされている間に更新または追加、更新は警告なしに破棄します。

使用して、`Move`条件を適用せず、レコード間を移動する関数。 ダイナセット タイプまたは特定の条件を満たすスナップショット タイプのレコード セット オブジェクトでレコードを検索するのにには、検索操作を使用します。 テーブル型のレコード セット オブジェクトでレコードを検索、呼び出す`Seek`します。

レコード セットは、テーブル型のレコード セットを参照している場合、移動には、テーブルの現在のインデックスに従います。 基になる DAO オブジェクトのインデックスのプロパティを使用して、現在のインデックスを設定できます。 場合は、現在のインデックスを設定しないと、返されるレコードの順序は定義されません。

呼び出す場合`MoveLast`SQL クエリまたはクエリに基づいて、レコード セット オブジェクトのクエリは強制的に完了して、レコード セット オブジェクトが完全に設定されます。

呼び出すことはできません、`MoveFirst`または`MovePrev`方向スクロールのスナップショットを使用してメンバー関数。

個のレコードを前方または後方の特定記録 recordset オブジェクトの現在の位置を移動するには、呼び出す`Move`します。

関連情報については、「メソッドの移動」トピックを参照してください。"MoveFirst、MoveLast、MoveNext、MovePrevious メソッド"と DAO のヘルプ。

##  <a name="movelast"></a>  CDaoRecordset::MoveLast

レコード セットの現在のレコードの最後のレコード (該当する場合) には、このメンバー関数を呼び出します。

```
void MoveLast();
```

### <a name="remarks"></a>Remarks

> [!CAUTION]
>  いずれかを呼び出し、`Move`レコード セットにレコードが存在しない場合、関数が例外をスローします。 一般に、両方を呼び出す`IsBOF`と`IsEOF`移動操作を任意のレコードをレコード セットが存在するかどうかを判断する前にします。 呼び出した後`Open`または`Requery`、いずれかを呼び出す`IsBOF`または`IsEOF`します。

> [!NOTE]
>  呼び出す場合、`Move`関数の現在のレコードがされている間に更新または追加、更新は警告なしに破棄します。

使用して、`Move`条件を適用せず、レコード間を移動する関数。 ダイナセット タイプまたは特定の条件を満たすスナップショット タイプのレコード セット オブジェクトでレコードを検索するのにには、検索操作を使用します。 テーブル型のレコード セット オブジェクトでレコードを検索、呼び出す`Seek`します。

レコード セットは、テーブル型のレコード セットを参照している場合、移動には、テーブルの現在のインデックスに従います。 基になる DAO オブジェクトのインデックスのプロパティを使用して、現在のインデックスを設定できます。 場合は、現在のインデックスを設定しないと、返されるレコードの順序は定義されません。

呼び出す場合`MoveLast`SQL クエリまたはクエリに基づいて、レコード セット オブジェクトのクエリは強制的に完了して、レコード セット オブジェクトが完全に設定されます。

個のレコードを前方または後方の特定記録 recordset オブジェクトの現在の位置を移動するには、呼び出す`Move`します。

関連情報については、「メソッドの移動」トピックを参照してください。"MoveFirst、MoveLast、MoveNext、MovePrevious メソッド"と DAO のヘルプ。

##  <a name="movenext"></a>  CDaoRecordset::MoveNext

レコード セットの現在のレコード内の次のレコードを作成するには、このメンバー関数を呼び出します。

```
void MoveNext();
```

### <a name="remarks"></a>Remarks

呼び出すことをお勧め`IsBOF`前のレコードに移動しようとする前にします。 呼び出し`MovePrev`がスローされます、`CDaoException`場合`IsBOF`0 以外の場合、最初のレコードの前に既にスクロールしたか、レコードがレコード セットが選択されていないことを示すを返します。

> [!CAUTION]
>  いずれかを呼び出し、`Move`レコード セットにレコードが存在しない場合、関数が例外をスローします。 一般に、両方を呼び出す`IsBOF`と`IsEOF`移動操作を任意のレコードをレコード セットが存在するかどうかを判断する前にします。 呼び出した後`Open`または`Requery`、いずれかを呼び出す`IsBOF`または`IsEOF`します。

> [!NOTE]
>  呼び出す場合、`Move`関数の現在のレコードがされている間に更新または追加、更新は警告なしに破棄します。

使用して、`Move`条件を適用せず、レコード間を移動する関数。 ダイナセット タイプまたは特定の条件を満たすスナップショット タイプのレコード セット オブジェクトでレコードを検索するのにには、検索操作を使用します。 テーブル型のレコード セット オブジェクトでレコードを検索、呼び出す`Seek`します。

レコード セットは、テーブル型のレコード セットを参照している場合、移動には、テーブルの現在のインデックスに従います。 基になる DAO オブジェクトのインデックスのプロパティを使用して、現在のインデックスを設定できます。 場合は、現在のインデックスを設定しないと、返されるレコードの順序は定義されません。

個のレコードを前方または後方の特定記録 recordset オブジェクトの現在の位置を移動するには、呼び出す`Move`します。

関連情報については、「メソッドの移動」トピックを参照してください。"MoveFirst、MoveLast、MoveNext、MovePrevious メソッド"と DAO のヘルプ。

##  <a name="moveprev"></a>  CDaoRecordset::MovePrev

現在のレコードをレコード セットの前のレコードを作成するには、このメンバー関数を呼び出します。

```
void MovePrev();
```

### <a name="remarks"></a>Remarks

呼び出すことをお勧め`IsBOF`前のレコードに移動しようとする前にします。 呼び出し`MovePrev`がスローされます、`CDaoException`場合`IsBOF`0 以外の場合、最初のレコードの前に既にスクロールしたか、レコードがレコード セットが選択されていないことを示すを返します。

> [!CAUTION]
>  いずれかを呼び出し、`Move`レコード セットにレコードが存在しない場合、関数が例外をスローします。 一般に、両方を呼び出す`IsBOF`と`IsEOF`移動操作を任意のレコードをレコード セットが存在するかどうかを判断する前にします。 呼び出した後`Open`または`Requery`、いずれかを呼び出す`IsBOF`または`IsEOF`します。

> [!NOTE]
>  呼び出す場合、`Move`関数の現在のレコードがされている間に更新または追加、更新は警告なしに破棄します。

使用して、`Move`条件を適用せず、レコード間を移動する関数。 ダイナセット タイプまたは特定の条件を満たすスナップショット タイプのレコード セット オブジェクトでレコードを検索するのにには、検索操作を使用します。 テーブル型のレコード セット オブジェクトでレコードを検索、呼び出す`Seek`します。

レコード セットは、テーブル型のレコード セットを参照している場合、移動には、テーブルの現在のインデックスに従います。 基になる DAO オブジェクトのインデックスのプロパティを使用して、現在のインデックスを設定できます。 場合は、現在のインデックスを設定しないと、返されるレコードの順序は定義されません。

呼び出すことはできません、`MoveFirst`または`MovePrev`方向スクロールのスナップショットを使用してメンバー関数。

個のレコードを前方または後方の特定記録 recordset オブジェクトの現在の位置を移動するには、呼び出す`Move`します。

関連情報については、「メソッドの移動」トピックを参照してください。"MoveFirst、MoveLast、MoveNext、MovePrevious メソッド"と DAO のヘルプ。

##  <a name="open"></a>  CDaoRecordset::Open

レコード セットのレコードを取得するには、このメンバー関数を呼び出す必要があります。

```
virtual void Open(
    int nOpenType = AFX_DAO_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    int nOptions = 0);

virtual void Open(
    CDaoTableDef* pTableDef,
    int nOpenType = dbOpenTable,
    int nOptions = 0);

virtual void Open(
    CDaoQueryDef* pQueryDef,
    int nOpenType = dbOpenDynaset,
    int nOptions = 0);
```

### <a name="parameters"></a>パラメーター

*できるかどうか*<br/>
次のいずれかの値です。

- `dbOpenDynaset` 双方向にスクロールできるダイナセット タイプ レコード セット。 既定値です。

- `dbOpenTable` 双方向にスクロールできるタイプのレコード。

- `dbOpenSnapshot` 双方向にスクロールできるスナップショットの種類のレコード セット。

*lpszSQL*<br/>
次のいずれかを含む文字列ポインター:

- NULL のポインター。

- テーブル定義やクエリ定義の (コンマ区切り) の 1 つまたは複数の名前。

- SQL**SSELECT**ステートメント (SQL オプションで**WHERE**または**ORDERBY**句)。

- パススルー クエリです。

*nOptions*<br/>
1 つ以上の次のオプション。 既定値は 0 です。 次の値を指定できます。

- `dbAppendOnly` 新しいレコード (ダイナセット タイプのレコード セットのみ) にのみ追加できます。 このオプションは、文字どおりレコードを追加のみことができます。 MFC ODBC データベース クラスには、レコードの取得し、追加可能追加専用オプションが用意されています。

- `dbForwardOnly` レコード セットは、順方向専用のスクロール スナップショットです。

- `dbSeeChanges` 別のユーザーが編集してデータを変更する場合は、例外を生成します。

- `dbDenyWrite` 他のユーザーは、変更またはレコードを追加することはできません。

- `dbDenyRead` 他のユーザーには、レコード (タイプのレコードのみ) を表示できません。

- `dbReadOnly` レコードのみを表示できます。他のユーザーを変更できます。

- `dbInconsistent` 一貫性のない更新を許可 (ダイナセット タイプのレコード セットのみ)。

- `dbConsistent` 一貫性のある更新のみを許可 (ダイナセット タイプのレコード セットのみ)。

> [!NOTE]
>  定数`dbConsistent`と`dbInconsistent`は相互に排他的です。 いずれかを使用するか、一方の特定のインスタンスの両方ではなく`Open`します。

*pTableDef*<br/>
ポインターを[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)オブジェクト。 このバージョンは、テーブル型のレコード セットに対してのみ有効です。 、このオプションを使用する場合、`CDaoDatabase`ポインターの構築に使用される、`CDaoRecordset`は使用されません。 代わりに、テーブル定義が存在するデータベースが使用されます。

*pQueryDef*<br/>
ポインターを[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)オブジェクト。 このバージョンはダイナセット タイプとスナップショットの種類のレコード セットに対してのみ有効です。 このオプションを使用する場合、`CDaoDatabase`ポインターの構築に使用される、`CDaoRecordset`は使用されません。 ではなく、クエリ定義が存在するデータベースが使用されます。

### <a name="remarks"></a>Remarks

呼び出しの前に`Open`、レコード セット オブジェクトを構築する必要があります。 これにはいくつかの方法があります。

- レコード セット オブジェクトを構築する場合へのポインターを渡す、`CDaoDatabase`既に開かれているオブジェクト。

- レコード セット オブジェクトを構築する場合へのポインターを渡す、`CDaoDatabase`が開いていないオブジェクト。 レコード セットが表示されます、`CDaoDatabase`オブジェクトしますが、レコード セット オブジェクトを閉じるときに、その閉じるされません。

- レコード セット オブジェクトを構築するときは、NULL ポインターを渡します。 レコード セット オブジェクトの呼び出し`GetDefaultDBName`Microsoft Access の名前を取得します。MDB ファイルを開きます。 レコード セットを開きます、`CDaoDatabase`オブジェクトと、レコード セットが開く限りを開くことができます。 呼び出すと`Close`、レコード セットに対して、`CDaoDatabase`オブジェクトも閉じられます。

    > [!NOTE]
    >  レコード セットが開かれたとき、`CDaoDatabase`オブジェクト、非独占的なアクセス権を持つデータ ソースを開きます。

バージョンの`Open`を使用して、 *lpszSQL*パラメーター、いくつかの方法の 1 つのレコードを取得するには、レコード セットが開く。 最初のオプションが DFX 関数には、`DoFieldExchange`します。 2 番目のオプションは、呼び出すことによって動的バインドを使用する、`GetFieldValue`メンバー関数。 これらのオプションは、個別または組み合わせて実装できます。 結合を渡す SQL ステートメントで自分自身への呼び出しで必要があります`Open`します。

2 番目のバージョンを使用すると`Open`で渡せば、`CDaoTableDef`オブジェクトを使用してバインドすることのできる結果として得られる列`DoFieldExchange`と DFX メカニズム、または使用して動的にバインド`GetFieldValue`します。

> [!NOTE]
>  のみ呼び出すことができます`Open`を使用して、`CDaoTableDef`テーブル タイプのレコード セットのオブジェクト。

3 番目のバージョンを使用すると`Open`で渡せば、`CDaoQueryDef`オブジェクト、クエリは実行され、その結果として得られる列を使用してバインドできるようになります`DoFieldExchange`と DFX メカニズム、または使用して動的にバインド`GetFieldValue`します。

> [!NOTE]
>  のみ呼び出すことができます`Open`を使用して、`CDaoQueryDef`ダイナセット タイプおよびスナップショット タイプのレコード セットのオブジェクト。

最初のバージョンの`Open`を使用して、`lpszSQL`パラメーター、レコードは、次の表に示すように条件がに基づいて選択します。

|パラメーター `lpszSQL` の値。|レコードの選択基準|例|
|--------------------------------------|----------------------------------------|-------------|
|NULL|`GetDefaultSQL` の返す文字列。||
|1 つまたは複数のテーブル定義やクエリ定義名のコンマ区切りの一覧。|表されるすべての列、`DoFieldExchange`します。|`"Customer"`|
|**SELECT** 列リスト **FROM** テーブル リスト|指定されたテーブルまたはクエリ定義から指定された列です。|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

通常のプロシージャでは NULL を`Open`。 その場合、`Open`呼び出し`GetDefaultSQL`、ClassWizard 生成の作成時にオーバーライド可能なメンバー関数、 `CDaoRecordset`-クラスを派生します。 この値は、ClassWizard で指定したテーブルやクエリ定義の名前を示します。 代わりにその他の情報を指定することができます、 *lpszSQL*パラメーター。

渡したもの`Open`クエリの最終的な SQL 文字列を構築します (SQL も**WHERE**と**ORDERBY**句が追加された、 *lpszSQL*文字列渡されたする) し、クエリを実行します。 呼び出すことによって作成された文字列を調べることができます`GetSQL`呼び出した後`Open`します。

レコードセット クラスのフィールド データ メンバーは、選択したデータの列に結び付けられています。 いくつかのレコードが返された場合、最初のレコードが現在のレコードになります。

レコード セットは、フィルターや並べ替えなどのオプションを設定する場合は、設定`m_strSort`または`m_strFilter`を呼び出す前に、レコード セット オブジェクトの構築後`Open`します。 レコード セットがまだ開いて後にレコード セットのレコードを更新する場合、呼び出す`Requery`します。

呼び出す場合`Open`ダイナセット型またはスナップショットの種類のレコード セットに使用することはできません、SQL ステートメントまたはアタッチ テーブルを表すテーブル定義が、データ ソースが参照されている場合、または`dbOpenTable`は型引数の場合は、MFC 例外をスローします。 テーブル定義のオブジェクトが接続されているテーブルを表すかどうかを確認するのには、作成、 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)オブジェクトと呼び出しの[GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect)メンバー関数。

使用して、`dbSeeChanges`同じレコードを削除または編集するときに、別のユーザーまたはコンピューターに別のプログラムによって行われた変更をトラップする場合にフラグを設定します。 たとえば、2 人のユーザーが同じのレコードを呼び出す最初のユーザーの編集を開始、`Update`メンバー関数が成功するとします。 ときに`Update`2 番目のユーザーによって呼び出される、`CDaoException`がスローされます。 同様に、2 番目のユーザーが呼び出しを試みると`Delete`、レコードとそれを削除するが既に変更されて、最初のユーザーによって、`CDaoException`に発生します。

通常、ユーザーがこの場合`CDaoException`の更新中に、コードする必要があります、フィールドの内容を更新し、新しく変更された値を取得します。 削除中に例外が発生した場合、コードは、データが最近変更されたことを示すメッセージをユーザーに新しいレコード データを表示する可能性があります。 この時点で、コードでは、ユーザーがレコードを削除してもよいことの確認を要求できます。

> [!TIP]
>  順方向専用のスクロール オプションを使用して (`dbForwardOnly`) アプリケーションでレコード セットを 1 つのパスと、パフォーマンスを向上させるために、ODBC データ ソースから開きます。

関連情報については、「何らかのメソッド」DAO ヘルプのトピックを参照してください。

##  <a name="requery"></a>  CDaoRecordset::Requery

レコード セット (更新) を再構築するには、このメンバー関数を呼び出します。

```
virtual void Requery();
```

### <a name="remarks"></a>Remarks

いくつかのレコードが返された場合、最初のレコードが現在のレコードになります。

追加と削除または他のユーザーがデータ ソースに行っているを反映するようにレコード セットの順序で呼び出すことによって、レコード セットをリビルドする必要があります`Requery`します。 レコード セットがダイナセットである場合は、または他のユーザーがその既存のレコード (ただし、追加機能ではない) を構成する更新プログラムが自動的に反映します。 呼び出す必要がある、レコード セットがスナップショットである場合は、`Requery`編集内容を他のユーザーだけでなく追加および削除を反映するようにします。

ダイナセットまたはスナップショットのいずれかを呼び出す`Requery`パラメーターの値を使用してレコード セットを再構築する任意の時間。 設定して、新しいフィルターまたは並べ替えを設定する[か](#m_strfilter)と[レコード](#m_strsort)呼び出す前に`Requery`します。 新しい値を呼び出す前にパラメーターのデータ メンバーに割り当てることで新しいパラメーターを設定`Requery`します。

レコード セットを再構築に失敗した場合、レコード セットが閉じられます。 呼び出す前に`Requery`、呼び出すことによって、レコード セットを表示できるかどうかを指定できます、 [CanRestart](#canrestart)メンバー関数。 `CanRestart` いるは限りません`Requery`は成功します。

> [!CAUTION]
>  呼び出す`Requery`を呼び出した後にのみ`Open`します。

> [!NOTE]
>  呼び出す[Requery](#requery) DAO のブックマークを変更します。

呼び出すことはできません`Requery`ダイナセット型またはスナップショットの種類のレコード セットを呼び出す場合に`CanRestart`0 を返しますそれを使用してテーブル型のレコード セットにもします。

両方`IsBOF`と`IsEOF`呼び出した後に 0 以外を返す`Requery`、すべてのレコードとレコード セットはデータを格納、クエリが返されませんでした。

関連情報については、「Requery メソッド」DAO ヘルプのトピックを参照してください。

##  <a name="seek"></a>  CDaoRecordset::Seek

指定した条件を現在のインデックスし、そのレコードを現在のレコードを満たすインデックス付きのテーブル型のレコード セット オブジェクト内でレコードを検索するには、このメンバー関数を呼び出します。

```
BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKey1,
    COleVariant* pKey2 = NULL,
    COleVariant* pKey3 = NULL);

BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKeyArray,
    WORD nKeys);
```

### <a name="parameters"></a>パラメーター

*lpszComparison*<br/>
次の文字列式のいずれか:"<「、」\<="、「=」、"> ="、または">"。

*pKey1*<br/>
ポインターを[COleVariant](../../mfc/reference/colevariant-class.md)値を持つが、インデックスの最初のフィールドに対応します。 必須。

*pKey2*<br/>
ポインターを`COleVariant`値が存在する場合、インデックスの 2 つ目のフィールドに対応します。 既定値は NULL です。

*pKey3*<br/>
ポインターを`COleVariant`値が存在する場合、インデックスの 3 番目のフィールドに対応します。 既定値は NULL です。

*pKeyArray*<br/>
Variant の配列へのポインター。 配列のサイズは、インデックスのフィールドの数に対応します。

*nKeys*<br/>
これは、インデックス内のフィールドの数と、配列のサイズに対応する整数。

> [!NOTE]
>  キーでは、ワイルドカードを指定しません。 ワイルドカードと、`Seek`から一致するレコードが返されない。

### <a name="return-value"></a>戻り値

一致するレコードが見つかった場合、それ以外の場合 0 0 以外の値。

### <a name="remarks"></a>Remarks

2 つ目の (配列) のバージョンを使用して、`Seek`以上の 4 つのフィールドのインデックスを処理します。

`Seek` 高パフォーマンスのインデックスがテーブル タイプのレコード セットの検索を有効にします。 呼び出すことによって、現在のインデックスを設定する必要があります`SetCurrentIndex`呼び出す前に`Seek`します。 インデックスが一意のキー フィールドまたはフィールドを指定する場合`Seek`に条件を満たす最初のレコードを見つけます。 インデックスを設定しないと、例外がスローされます。

UNICODE のレコード セットを作成していない場合、`COleVariant`オブジェクトに明示的に宣言される ANSI です。 これを使用して行うことができます、 [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **(** *lpszSrc* **、** *vtSrc* **)** 形式を持つコンス トラクターの*vtSrc*設定`VT_BSTRT`(ANSI) またはを使用して、`COleVariant`関数[SetString](../../mfc/reference/colevariant-class.md#setstring) **(** *lpszSrc* **、** *vtSrc* **)** で*vtSrc*設定`VT_BSTRT`します。

呼び出すと`Seek`、渡す 1 つまたは複数のキー値と比較演算子 ("<「、」\<="、「=」、"> ="、または">")。 `Seek` 指定されたキー フィールドを検索しで指定された条件を満たす最初のレコードを見つけます*lpszComparison*と*pKey1*します。 見つかると、 `Seek` 、0 以外を返すし、そのレコードは現在、します。 場合`Seek`一致を見つけが失敗した`Seek`0 が返されます、および現在のレコードが定義されていません。 DAO の直接を使用する場合は、NoMatch プロパティを明示的にチェックする必要があります。

場合`lpszComparison`は「=」"> ="、または">"、`Seek`インデックスの先頭から開始されます。 場合*lpszComparison*は"<"または"< ="、`Seek`インデックスの最後に起動し、最後に重複するインデックス エントリがある場合を除き、逆方向に検索します。 この場合、`Seek`インデックスの最後に重複するインデックス エントリの間での任意のエントリから始まります。

現在のレコードを使用するときにする必要はありません`Seek`します。

ダイナセット タイプまたは特定の条件を満たすスナップショット タイプのレコード セットのレコードを検索するには、検索操作を使用します。 特定の条件を満たすものだけでなく、すべてのレコードを含めるには、レコード間を移動する移動操作を使用します。

呼び出すことはできません`Seek`アタッチ テーブルのいずれかでダイナセット タイプまたはスナップショットの種類のレコード セットとしてアタッチされているテーブルを開く必要があるために、入力します。 ただし、呼び出す場合`CDaoDatabase::Open`インストール可能な ISAM データベースを直接開き、呼び出すことができます`Seek`、そのデータベース内のテーブルにありますが、パフォーマンスが低下します。

関連情報については、「DAO ヘルプの「メソッドのシーク」」を参照してください。

##  <a name="setabsoluteposition"></a>  CDaoRecordset::SetAbsolutePosition

レコード セット オブジェクトの現在のレコードの相対レコード数を設定します。

```
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>パラメーター

*lPosition*<br/>
レコード セット内の現在のレコードの序数位置に対応します。

### <a name="remarks"></a>Remarks

呼び出す`SetAbsolutePosition`ダイナセット型、またはスナップショットの種類のレコード セットの序数位置に基づいて、特定のレコードを現在のレコード ポインターを配置することができます。 呼び出すことによって、現在のレコード番号を確認することも[GetAbsolutePosition](#getabsoluteposition)します。

> [!NOTE]
>  このメンバー関数がダイナセット タイプとスナップショットの種類のレコード セットに対してのみ有効です。

基になる DAO オブジェクトの AbsolutePosition プロパティの値が 0 から始まります。0 の設定は、レコード セットの最初のレコードを表します。 データが設定されたレコードと、例外をスローする MFC の数より大きい値を設定します。 呼び出すことによって、レコード セット内のデータが設定されたレコードの数を判断する、`GetRecordCount`メンバー関数。

現在のレコードが削除された場合、AbsolutePosition プロパティの値が定義されていないと、MFC は、参照されている場合に例外をスローします。 新しいレコードは、シーケンスの末尾に追加されます。

> [!NOTE]
>  このプロパティは、レコード番号の代わりとして使用するものではありません。 ブックマークが保持して、指定した位置に戻るをお勧めであり、あらゆる種類のブックマークをサポートするレコード セット オブジェクトの現在のレコードを配置する唯一の方法。 具体的には、前のレコードが削除されたときに特定のレコードの位置を変更します。 また、レコード セットを再作成を使用して SQL ステートメントで作成されたレコード セット内の各レコードの順序が保証されないため場合、特定のレコードが同じ絶対位置を持つことの保証はありません、 **ORDERBY**句。

関連情報については、「AbsolutePosition プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="setbookmark"></a>  CDaoRecordset::SetBookmark

指定されたブックマークを含むレコードをレコード セットに移動するには、このメンバー関数を呼び出します。

```
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>パラメーター

*varBookmark*<br/>
A [COleVariant](../../mfc/reference/colevariant-class.md)特定のレコードのブックマークの値を格納しているオブジェクト。

### <a name="remarks"></a>Remarks

レコード セット オブジェクトを作成したり開いたりすると、各レコードは既に一意のブックマークを持っています。 呼び出すことによって、現在のレコードのブックマークを取得する`GetBookmark`に値を保存して、`COleVariant`オブジェクト。 後で呼び出すことでそのレコードに戻すことができます`SetBookmark`保存されているブックマークの値を使用します。

> [!NOTE]
>  呼び出す[Requery](#requery) DAO のブックマークを変更します。

UNICODE のレコード セットを作成していない場合、`COleVariant`オブジェクトに明示的に宣言される ANSI です。 これを使用して行うことができます、 [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **(** *lpszSrc* **、** *vtSrc* **)** 形式を持つコンス トラクターの*vtSrc*設定`VT_BSTRT`(ANSI) またはを使用して、`COleVariant`関数[SetString](../../mfc/reference/colevariant-class.md#setstring) **(** *lpszSrc* **、** *vtSrc* **)** で*vtSrc*設定`VT_BSTRT`します。

関連情報については、トピックを参照して、「Bookmark プロパティ」とブックマークを設定のプロパティ"DAO のヘルプ。

##  <a name="setcachesize"></a>  CDaoRecordset::SetCacheSize

キャッシュするレコードの数を設定するには、このメンバー関数を呼び出します。

```
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>パラメーター

*lSize*<br/>
レコードの数を指定します。 標準的な値は 100 です。 0 に設定は、キャッシュをオフにします。 設定は、5 ~ 1200 レコード間で指定する必要があります。 キャッシュは、相当量のメモリを使用できます。

### <a name="remarks"></a>Remarks

キャッシュは、サーバーから、アプリケーションの実行中にデータをもう一度要求は、最も最近取得されたデータを保持するローカル メモリ内のスペースです。 データ キャッシュでは、ダイナセット タイプのレコード セット オブジェクトを使用してリモート サーバーからデータを取得するアプリケーションのパフォーマンスが向上します。 データが要求されると、Microsoft Jet データベース エンジンまず要求されたデータのキャッシュ時間がかかると、サーバーから取得するのではなく。 ODBC データ ソースから発生しないデータがキャッシュに保存されません。

アタッチのテーブルなど、任意の ODBC データ ソースには、ローカル キャッシュを持つことができます。 キャッシュを作成するには、リモート データ ソース、呼び出しから recordset オブジェクトを開く、`SetCacheSize`と`SetCacheStart`メンバー関数と、呼び出し、`FillCache`メンバー関数または移動操作のいずれかを使用して、レコード間のステップ。 *LSize*のパラメーター、`SetCacheSize`メンバー関数は、アプリケーションが同時に使用できるレコードの数に基づくことができます。 たとえば、画面に表示されるデータのソースとして、レコード セットを使用する場合を渡すことができます、 `SetCacheSize` *lSize*パラメーターに 20 を同時に 20 個のレコードを表示します。

関連情報については、DAO のヘルプ トピック"CacheSize CacheStart プロパティ"を参照してください。

##  <a name="setcachestart"></a>  CDaoRecordset::SetCacheStart

キャッシュするレコード セットの最初のレコードのブックマークを指定するには、このメンバー関数を呼び出します。

```
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>パラメーター

*varBookmark*<br/>
A [COleVariant](../../mfc/reference/colevariant-class.md)キャッシュするレコード セットの最初のレコードのブックマークを指定します。

### <a name="remarks"></a>Remarks

任意のレコードのブックマークの値を使用することができます、 *varBookmark*のパラメーター、`SetCacheStart`メンバー関数。 現在のレコードにキャッシュを開始、そのレコードを使用するためのブックマークを確立するレコード[SetBookmark](#setbookmark)、ブックマーク値のパラメーターとして渡すと、`SetCacheStart`メンバー関数。

Microsoft Jet データベース エンジンが、キャッシュからキャッシュの範囲内のレコードを要求し、サーバーからのキャッシュの範囲外のレコードを要求します。

キャッシュから取得したレコードには、他のユーザーがデータ ソースに同時に行われた変更は反映されません。

キャッシュされたすべてのデータの更新プログラムを強制的に渡す、 *lSize*パラメーターの`SetCacheSize`0 として呼び出す`SetCacheSize`もう一度、キャッシュのサイズを最初に要求を呼び出して、`FillCache`メンバー関数。

UNICODE のレコード セットを作成していない場合、`COleVariant`オブジェクトに明示的に宣言される ANSI です。 これを使用して行うことができます、 [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **(** *lpszSrc* **、** *vtSrc* **)** 形式を持つコンス トラクターの*vtSrc*設定`VT_BSTRT`(ANSI) またはを使用して、`COleVariant`関数[SetString](../../mfc/reference/colevariant-class.md#setstring) **(** *lpszSrc* **、** *vtSrc* **)** で*vtSrc*設定`VT_BSTRT`します。

関連情報についてを参照してください、CacheSize CacheStart プロパティ"DAO のヘルプします。

##  <a name="setcurrentindex"></a>  CDaoRecordset::SetCurrentIndex

テーブル型のレコード セットのインデックスを設定するには、このメンバー関数を呼び出します。

```
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>パラメーター

*lpszIndex*<br/>
設定するインデックスの名前を示すポインター。

### <a name="remarks"></a>Remarks

ベース テーブルのレコードは、特定の順序では保存されません。 インデックスを設定すると、データベースから返されるレコードの順序変更が、レコードが格納されている順序には影響しません。 指定したインデックスは、既に定義されている必要があります。 存在しないインデックス オブジェクトを使用しようとする場合、または呼び出すときに、インデックスが設定されていない場合[シーク](#seek)、MFC 例外をスローします。

テーブルの新しいインデックスを作成するには呼び出すことによって[CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex)を呼び出すことによって、基になるテーブルのインデックスのコレクションに新しいインデックスを追加すること[CDaoTableDef::Append](../../mfc/reference/cdaotabledef-class.md#append)とレコード セットを閉じてください。

テーブル型のレコード セットから返されるレコードは、基になるテーブルに対して定義されているインデックスだけが注文できます。 その他の順序でレコードを並べ替えるには、ダイナセット型または SQL を使用して、スナップショットの種類のレコード セットを開くことができます**ORDERBY**に格納されている句[CDaoRecordset::m_strSort](#m_strsort)します。

関連情報については、トピック「インデックス オブジェクト」および DAO のヘルプでは、"現在のインデックス"の定義を参照してください。

##  <a name="setfielddirty"></a>  CDaoRecordset::SetFieldDirty

このメンバー関数として、変更の有無、レコード セットのフィールド データ メンバーのフラグを呼び出します。

```
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>パラメーター

*現在価値*<br/>
レコード セットのフィールド データ メンバーのアドレスが含まれています。 NULL の場合、レコード セット内のすべてのフィールド データ メンバーのフラグが設定されます。 (C++ の NULL は Null の場合と同じデータベース用語では、「値を持たない」を意味する)。

*bDirty*<br/>
フィールド データ メンバーは、「ダーティ」(変更) としてフラグを設定する場合は TRUE。 「クリーン」(変更されていない) としてフラグを設定する場合は、フィールド データ メンバーの場合は FALSE。

### <a name="remarks"></a>Remarks

フィールドの変更をマークすることにより、フィールドは更新されません。

フレームワークでは、フィールド データ メンバーに DAO レコード フィールド エクス (チェンジ DFX) メカニズムによって、データ ソースのレコードに記述が変更されました。 フィールドの値を変更すると、通常フィールド ダーティ設定、自動的に呼び出す必要はめったにありません`SetFieldDirty`が、自分でことがありますようにすることも、列が明示的に更新または挿入フィールドのデータがどのような値に関係なくメンバー。 DFX メカニズムには、PSEUDONULL の使用も採用されています。 詳細については、次を参照してください。 [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)します。

ダブル バッファリング機構を使用しない場合、フィールドの値を変更して自動的に設定しませんフィールド ダーティとして。 この場合、フィールドをダーティとして明示的に設定する必要があります。 含まれているフラグ[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)このフィールドの自動チェックを制御します。

> [!NOTE]
>  呼び出した後にのみ、このメンバー関数を呼び出す[編集](#edit)または[AddNew](#addnew)します。

NULL を使用して、関数の最初の引数はすべてに、関数を適用する`outputColumn`フィールド、いない**param**フィールド`CDaoFieldExchange`します。 たとえば、呼び出し

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

設定時のみが`outputColumn`フィールドを NULL です。**param**フィールドが影響を受けません。

動作する、 **param**、個人の実際のアドレスを指定する必要があります**param**など、作業します。

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

つまり、すべてを設定することはできません**param**と同様に NULL フィールド`outputColumn`フィールド。

`SetFieldDirty` によって実装`DoFieldExchange`します。

##  <a name="setfieldnull"></a>  CDaoRecordset::SetFieldNull

(値を持たない) Null または null 以外のレコード セットのフィールド データ メンバーにフラグを設定するには、このメンバー関数を呼び出します。

```
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>パラメーター

*現在価値*<br/>
レコード セットのフィールド データ メンバーのアドレスが含まれています。 NULL の場合、レコード セット内のすべてのフィールド データ メンバーのフラグが設定されます。 (C++ の NULL は Null の場合と同じデータベース用語では、「値を持たない」を意味する)。

*bNull*<br/>
以外の値 (Null) がないものとしてフラグを設定する場合は、フィールド データ メンバー。 フィールド データ メンバーの非 Null としてフラグを設定する場合は 0 それ以外の場合。

### <a name="remarks"></a>Remarks

`SetFieldNull` バインドされているフィールドに使用されますが、`DoFieldExchange`メカニズム。

レコード セットに新しいレコードを追加するとすべてのフィールド データ メンバーが最初に Null 値を設定および「ダーティ」(変更) フラグが付けられます。 データ ソースからレコードを取得するときの列を既にが値か、null。 Null の場合、フィールドに適切でない場合、 [CDaoException](../../mfc/reference/cdaoexception-class.md)がスローされます。

たとえば、具体的には呼び出し、値を持っていない現在のレコードのフィールドを指定する場合、ダブル バッファリング メカニズムを使用している場合`SetFieldNull`で*特別*Null としてフラグを TRUE に設定します。 Null フィールドが対象としてマーク済みの値を指定したい場合、単にその新しい値を設定します。 Null フラグを削除する必要はありません`SetFieldNull`します。 フィールドを Null にできるかどうかを確認するのには、呼び出す[調べる](#isfieldnullable)します。

ダブル バッファリング機構を使用していない場合、フィールドの値を変更して自動的に設定しませんフィールドとして、ダーティと Null 以外。 具体的にはダーティと非 Null フィールドを設定する必要があります。 含まれているフラグ[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)このフィールドの自動チェックを制御します。

DFX メカニズムでは、PSEUDONULL の使用を採用しています。 詳細については、次を参照してください。 [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)します。

> [!NOTE]
>  呼び出した後にのみ、このメンバー関数を呼び出す[編集](#edit)または[AddNew](#addnew)します。

NULL を使用して、関数の最初の引数は、関数にのみ適用されます`outputColumn`フィールド、いない**param**フィールド`CDaoFieldExchange`します。 たとえば、呼び出し

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

設定時のみが`outputColumn`フィールドを NULL です。**param**フィールドが影響を受けません。

##  <a name="setfieldvalue"></a>  CDaoRecordset::SetFieldValue

序数の位置または文字列の値を変更することで、フィールドの値を設定するには、このメンバー関数を呼び出します。

```
virtual void SetFieldValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetFieldValue(
    int nIndex,
    const COleVariant& varValue);

void SetFieldValue(
    LPCTSTR lpszName,
    LPCTSTR lpszValue);

void SetFieldValue(
    int nIndex,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
フィールドの名前を含む文字列へのポインター。

*varValue*<br/>
参照を[COleVariant](../../mfc/reference/colevariant-class.md)フィールドの内容の値を含むオブジェクト。

*nIndex*<br/>
レコード セットのフィールド コレクションの (0 から始まる) 内のフィールドの序数位置を表す整数。

*lpszValue*<br/>
フィールドの内容の値を含む文字列へのポインター。

### <a name="remarks"></a>Remarks

使用`SetFieldValue`と[GetFieldValue](#getfieldvalue)実行時ではなく静的を使用してバインド列にフィールドに動的にバインドする、 [DoFieldExchange](#dofieldexchange)メカニズム。

UNICODE のレコード セットを作成していないいずれかの形式を使用する必要がありますに注意してください。`SetFieldValue`を格納していない、`COleVariant`パラメーター、または`COleVariant`オブジェクトに明示的に宣言される ANSI です。 これを使用して行うことができます、 [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **(** *lpszSrc* **、** *vtSrc* **)** 形式を持つコンス トラクターの*vtSrc*設定`VT_BSTRT`(ANSI) またはを使用して、`COleVariant`関数[SetString](../../mfc/reference/colevariant-class.md#setstring) **(** *lpszSrc* **、** *vtSrc* **)** で*vtSrc*設定`VT_BSTRT`します。

関連情報については、「フィールド オブジェクト」と「値プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="setfieldvaluenull"></a>  CDaoRecordset::SetFieldValueNull

フィールドに Null 値を設定するには、このメンバー関数を呼び出します。

```
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
0 から始まるインデックスで検索する場合、レコード セット内のフィールドのインデックス。

*lpszName*<br/>
名前で検索する場合、レコード セット内のフィールドの名前。

### <a name="remarks"></a>Remarks

C++ の NULL でないと null の場合、つまり、データベース用語では、同じ「価値がありません」。

関連情報については、「フィールド オブジェクト」と「値プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="setlockingmode"></a>  CDaoRecordset::SetLockingMode

レコード セットのロックの種類を設定するには、このメンバー関数を呼び出します。

```
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>パラメーター

*bPessimistic*<br/>
ロックの種類を示すフラグ。

### <a name="remarks"></a>Remarks

呼び出すとすぐにロックされているときに排他ロックが実際には、2 K のページを編集しているレコードを含む、`Edit`メンバー関数。 呼び出すと、ページはロックが、`Update`または`Close`メンバー関数、または、移動または検索操作のいずれか。

レコードの更新中にのみレコードを含む 2 K のページがロックされているときに、オプティミスティック ロックが有効、`Update`メンバー関数。

ページがロックされている場合は、他のユーザー レコードを編集できません同じページにします。 呼び出す場合`SetLockingMode`し 0 以外の値を渡すと別のユーザーには既にロックされているページ、呼び出すときに例外がスローされて`Edit`します。 他のユーザーは、ロックされたページからデータを読み取ることができます。

呼び出す場合`SetLockingMode`ゼロの値以降を呼び出す`Update`ページは、別のユーザーによってロックされていますが、中に例外が発生します。 別のユーザーによって、レコードに加えられた変更を参照してください (し、変更が失われます)、電話、`SetBookmark`ブックマーク値は、現在のレコードのメンバー関数。

ODBC データ ソースを使用する場合のロック モードはオプティミスティックは常にします。

##  <a name="setparamvalue"></a>  CDaoRecordset::SetParamValue

実行時に、レコード セット内のパラメーターの値を設定するには、このメンバー関数を呼び出します。

```
virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);

virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
クエリ定義のパラメーター コレクション内のパラメーターの数値の位置。

*var*<br/>
値を設定します。「解説」を参照してください。

*lpszName*<br/>
値を設定するパラメーターの名前。

### <a name="remarks"></a>Remarks

パラメーターは、レコード セットの SQL 文字列の一部として確立するが既に必要があります。 パラメーター名、またはコレクションのインデックス位置を使用してアクセスできます。

として設定する値を指定する`COleVariant`オブジェクト。 目的の値と型の設定については、`COleVariant`オブジェクト、クラスを参照してください。 [COleVariant](../../mfc/reference/colevariant-class.md)します。 UNICODE のレコード セットを作成していない場合、`COleVariant`オブジェクトに明示的に宣言される ANSI です。 これを使用して行うことができます、 [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **(** *lpszSrc* **、** *vtSrc* **)** 形式を持つコンス トラクターの*vtSrc*設定`VT_BSTRT`(ANSI) またはを使用して、`COleVariant`関数[SetString](../../mfc/reference/colevariant-class.md#setstring) **(** *lpszSrc* **、** *vtSrc* **)** で*vtSrc*設定`VT_BSTRT`します。

##  <a name="setparamvaluenull"></a>  CDaoRecordset::SetParamValueNull

パラメーターを Null 値に設定するには、このメンバー関数を呼び出します。

```
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
0 から始まるインデックスで検索する場合、レコード セット内のフィールドのインデックス。

*lpszName*<br/>
名前で検索する場合、レコード セット内のフィールドの名前。

### <a name="remarks"></a>Remarks

C++ の NULL でないと null の場合、つまり、データベース用語では、同じ「価値がありません」。

##  <a name="setpercentposition"></a>  CDaoRecordset::SetPercentPosition

レコード セット内のレコードに対する割合に基づいて、レコード セット オブジェクトの現在のレコードのおおよその場所を変更する値を設定するには、このメンバー関数を呼び出します。

```
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>パラメーター

*fPosition*<br/>
0 ～ 100 の値。

### <a name="remarks"></a>Remarks

移動することで最後のレコードを呼び出す前に、レコード セットをまず設定ダイナセット タイプまたはスナップショットの種類のレコード セットを使用する場合`SetPercentPosition`します。 呼び出す場合`SetPercentPosition`の移動量がの値で示されるようにアクセスするレコードの数に対しては、レコード セットを完全に設定するには、する前に[GetRecordCount](#getrecordcount)します。 移動できます最後のレコードを呼び出して`MoveLast`します。

呼び出す`SetPercentPosition`、その値に対応するおおよその位置にあるレコードが最新になった。

> [!NOTE]
>  呼び出す`SetPercentPosition`移動、レコード セット内の特定のレコードを現在のレコードはお勧めしません。 呼び出す、 [SetBookmark](#setbookmark)メンバー関数を使用します。

関連情報については、「PercentPosition プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="update"></a>  CDaoRecordset::Update

呼び出しの後にこのメンバー関数を呼び出し、`AddNew`または`Edit`メンバー関数。

```
virtual void Update();
```

### <a name="remarks"></a>Remarks

この呼び出しが完了するために必要な`AddNew`または`Edit`操作。

両方`AddNew`と`Edit`データ ソースに保存するため、追加または編集したデータが置かれているをエディット バッファーを準備します。 `Update` データを保存します。 マークまたは変更されたものとして検出されたフィールドのみ更新されます。

データ ソースは、トランザクションをサポートする場合は、`Update`呼び出し (とその対応する`AddNew`または`Edit`呼び出し)、トランザクションの一部です。

> [!CAUTION]
> 呼び出す場合`Update`最初にいずれかの操作を呼び出すこと`AddNew`または`Edit`、`Update`スロー、`CDaoException`します。 呼び出す場合`AddNew`または`Edit`、呼び出す必要があります`Update`を呼び出す前に[MoveNext](#movenext)またはレコード セットまたはデータ ソース接続を終了します。 それ以外の場合、その変更は通知なしで失われます。

レコードの時点からロックされたまま、レコード セット オブジェクトがマルチ ユーザー環境で排他ロックされると、`Edit`更新が完了するまでに使用されます。 レコード セットがロックされる場合、レコードがロックされているし、データベースで更新される直前に、編集前のレコードと比較します。 呼び出されるので、レコードが変更された場合`Edit`、`Update`操作が失敗して、MFC は、例外をスローします。 ロック モードを変更する`SetLockingMode`します。

> [!NOTE]
> オプティミスティック ロックは常に、ODBC およびインストール可能な ISAM などの外部データベース形式で使用します。

関連情報については、「AddNew メソッド」、「CancelUpdate メソッド」、「メソッドの削除」、「LastModified プロパティ」、"Update Method"および「EditMode プロパティ」DAO ヘルプのトピックを参照してください。

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDaoTableDef クラス](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoWorkspace クラス](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase クラス](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoQueryDef クラス](../../mfc/reference/cdaoquerydef-class.md)<br/>
