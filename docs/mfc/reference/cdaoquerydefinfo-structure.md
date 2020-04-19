---
title: CDaoQueryDefInfo 構造体
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDefInfo
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
ms.openlocfilehash: d88d919bb87f614d140d710aee9df3fdf4fd10bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399734"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo 構造体

`CDaoQueryDefInfo`構造体には、データ アクセス オブジェクト (DAO) に対して定義されているクエリ定義のオブジェクトに関する情報が含まれています。

## <a name="syntax"></a>構文

```
struct CDaoQueryDefInfo
{
    CString m_strName;               // Primary
    short m_nType;   // Primary
    COleDateTime m_dateCreated;      // Secondary
    COleDateTime m_dateLastUpdated;  // Secondary
    BOOL m_bUpdatable;               // Secondary
    BOOL m_bReturnsRecords;          // Secondary
    CString m_strSQL;                // All
    CString m_strConnect;            // All
    short m_nODBCTimeout;            // All
};
```

#### <a name="parameters"></a>パラメーター

*m_strName*<br/>
クエリ定義のオブジェクトの一意名します。 詳細については、「Name プロパティ」DAO ヘルプのトピックを参照してください。 呼び出す[CDaoQueryDef::GetName](../../mfc/reference/cdaoquerydef-class.md#getname)このプロパティを直接取得します。

*m_nType*<br/>
クエリ定義のオブジェクトの操作の型を示す値。 値は次のいずれかになります。

- `dbQSelect` 選択: クエリでは、レコードを選択します。

- `dbQAction` アクション: クエリを移動または変更データしますが、レコードは返されません。

- `dbQCrosstab` クロス集計など、クエリは、スプレッドシートのような形式でデータを返します。

- `dbQDelete` クエリが指定された行のセットを削除します。

- `dbQUpdate` クエリが一連のレコードを更新します。

- `dbQAppend` 追加するには、クエリは、テーブルまたはクエリの末尾に新しいレコードを追加します。

- `dbQMakeTable` テーブル-作成、クエリは、レコード セットから新しいテーブルを作成します。

- `dbQDDL` データ定義、クエリは、テーブルまたはその一部の構造に影響します。

- `dbQSQLPassThrough` パススルー: SQL ステートメントは、中間処理を行わなくても、データベース バックエンドに直接渡されます。

- `dbQSetOperation` 共用体、クエリは 2 つの指定したすべてのレコードからデータを含むスナップショット タイプのレコード セット オブジェクトを作成します。 または、重複するレコードのテーブルを削除します。 重複を含めるには、キーワードを追加**すべて**クエリ定義の SQL ステートメントでします。

- `dbQSPTBulk` 併用`dbQSQLPassThrough`クエリ レコードは返されませんを指定します。

> [!NOTE]
>  設定しない SQL パススルー クエリを作成する、`dbQSQLPassThrough`定数。 これは自動的に設定、Microsoft Jet データベース エンジンによってクエリ定義のオブジェクトを作成し、接続プロパティを設定します。

詳細については、「型のプロパティ」DAO ヘルプのトピックを参照してください。

*m_dateCreated*<br/>
日付とクエリ定義が作成された時刻。 直接クエリ定義が作成された日付を取得する、 [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated)のメンバー関数、`CDaoTableDef`テーブルに関連付けられているオブジェクト。 詳細については、以下のコメントを参照してください。 DAO のヘルプでは、「DateCreated プロパティの LastUpdated」のトピックを参照してください。

*m_dateLastUpdated*<br/>
日付とクエリ定義に加えられた最新の変更の時刻。 テーブルの最終更新日を直接取得する、 [GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated)クエリ定義のメンバー関数。 詳細については、以下のコメントを参照してください。 DAO のヘルプ トピックの"DateCreated プロパティの LastUpdated"を確認してください。

*m_bUpdatable*<br/>
クエリ定義のオブジェクトへの変更を行うことができるかどうかを示します。 このプロパティが TRUE の場合、クエリ定義は更新できます。それ以外の場合は。 更新可能では、クエリ定義オブジェクトのクエリ定義を変更することができますを意味します。 クエリ定義のオブジェクトの更新可能なプロパティが設定を TRUE にクエリの定義を更新する場合場合でも、結果のレコード セットは更新できません。 このプロパティを直接取得するには、呼び出すクエリ定義の[CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate)メンバー関数。 詳細については、「更新可能なプロパティ」DAO ヘルプのトピックを参照してください。

*m_bReturnsRecords*<br/>
外部データベースに SQL パススルー クエリがレコードを返すかどうかを示します。 このプロパティが TRUE の場合、クエリは、レコードを返します。 このプロパティを直接取得するには、する[CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords)します。 外部データベースへのすべての SQL パススルー クエリには、レコードが返されます。 たとえば、SQL**更新**ステートメントは、SQL の中に、レコードを返さずにレコードを更新**選択**ステートメントはレコードが返されます。 詳細については、「レコード表示プロパティ」DAO ヘルプのトピックを参照してください。

*m_strSQL*<br/>
クエリ定義のオブジェクトによって実行されるクエリを定義する SQL ステートメント。 SQL プロパティには、どのレコードが選択、グループ化、順序付けられたクエリを実行するときに決定する SQL ステートメントが含まれています。 ダイナセット、またはスナップショットの種類のレコード セット オブジェクトに含めるレコードを選択するのにクエリを使用することができます。 レコードを返さずにデータを変更する一括クエリを定義することもできます。 このプロパティの値を取得するには、クエリ定義を呼び出すことによって直接[GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql)メンバー関数。

*m_strConnect*<br/>
パススルー クエリで使用されるデータベースのソースに関する情報を提供します。 この情報は、接続文字列の形式をとります。 詳細については、文字列を約接続し、このプロパティの値を直接取得する方法の詳細については、次を参照してください。、 [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect)メンバー関数。

*m_nODBCTimeout*<br/>
Microsoft Jet データベース エンジンがタイムアウト エラーが発生する前に待機する秒数では、ODBC データベース クエリの実行時に発生します。 Microsoft SQL Server など、ODBC データベースを使用しているときに、ODBC のサーバーのネットワーク トラフィックや負荷の高い使用しているため遅延が発生する可能性がありますがあります。 無限に待機するのではなく、Microsoft Jet エンジンがエラーを生成するまで待機する時間を指定できます。 既定のタイムアウト値は、60 秒です。 このプロパティの値を取得するには、クエリ定義を呼び出すことによって直接[GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout)メンバー関数。 詳細については、DAO ヘルプの「補足プロパティ」を参照してください。

## <a name="remarks"></a>Remarks

クエリ定義がクラスのオブジェクト[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)します。 プライマリ、セカンダリ、および上記のすべてへの参照情報がによって返される方法を示すため、 [GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo)クラスのメンバー関数`CDaoDatabase`します。

によって取得される情報、 [CDaoDatabase::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo)にメンバー関数が格納されている、`CDaoQueryDefInfo`構造体。 呼び出す`GetQueryDefInfo`QueryDefs コレクションでのクエリ定義のオブジェクトが格納されているデータベース オブジェクト。 `CDaoQueryDefInfo` 定義、`Dump`デバッグでのメンバー関数を作成します。 使用することができます`Dump`の内容をダンプする`CDaoQueryDefInfo`オブジェクト。 クラス`CDaoDatabase`で返されるプロパティのすべてに直接アクセスするためのメンバー関数が用意されても、`CDaoQueryDefInfo`オブジェクトを呼び出す必要がありますおそらくほとんど`GetQueryDefInfo`。

クエリ定義のオブジェクトのフィールドまたはパラメーターのコレクションに新しいフィールドまたはパラメーター オブジェクトを追加する場合は、基になるデータベースは、新しいオブジェクトの指定されたデータ型をサポートしていない場合、例外がスローされます。

日付と時刻の設定は、クエリ定義が作成または最後に更新されたコンピューターから派生します。 マルチ ユーザー環境では、ユーザーは、使用して、ファイル サーバーから直接これらの設定を取得する必要があります、**時間を net** DateCreated および LastUpdated プロパティの設定の不一致を避けるためのコマンド。

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdao.h

## <a name="see-also"></a>関連項目

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef クラス](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase クラス](../../mfc/reference/cdaodatabase-class.md)
