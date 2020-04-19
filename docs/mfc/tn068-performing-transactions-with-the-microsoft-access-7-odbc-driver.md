---
title: TN068:Microsoft Access 7 ODBC ドライバーを使用したトランザクションを実行します。
ms.date: 06/28/2018
f1_keywords:
- vc.data.odbc
helpviewer_keywords:
- TN068 [MFC]
- transactions [MFC], calling BeginTrans
- transactions [MFC], Microsoft Access
ms.assetid: d3f8f5d9-b118-4194-be36-a1aefb630c45
ms.openlocfilehash: 3121587f85c4ea19cc92e39569008b597d24ea58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363792"
---
# <a name="tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver"></a>TN068:Microsoft Access 7 ODBC ドライバーを使用したトランザクションを実行します。

> [!NOTE]
> 次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

ここでは、MFC ODBC データベース クラスと Microsoft ODBC Desktop ドライバー Pack バージョン 3.0 に含まれる Microsoft Access 7.0 ODBC ドライバーを使用する場合は、トランザクションを実行する方法について説明します。

## <a name="overview"></a>概要

データベース アプリケーションでは、トランザクションを実行する場合に呼び出す注意する必要があります`CDatabase::BeginTrans`と`CRecordset::Open`アプリケーションで、正しい順序で。 Microsoft Access 7.0 ドライバーは、Microsoft Jet データベース エンジンを使用して、Jet では、アプリケーションでは、開いているカーソルのある任意のデータベースでトランザクションを開始できないことが必要です。 MFC ODBC データベース クラスの開いているカーソルは、オープンに割り当てられる総合`CRecordset`オブジェクト。

呼び出しの前にレコード セットを開く場合`BeginTrans`、すべてのエラー メッセージが表示されない場合があります。 ただし、すべてのレコード セットは更新呼び出した後に永続的に、アプリケーションが`CRecordset::Update`、更新プログラムはロールバックされませんを呼び出して、`Rollback`します。 この問題を回避するために呼び出す必要がある`BeginTrans`最初し、レコード セットを開きます。

MFC は、カーソルのコミットとロールバックの動作のドライバーの機能を確認します。 クラス`CDatabase`2 つのメンバー関数は、`GetCursorCommitBehavior`と`GetCursorRollbackBehavior`、開くときに、トランザクションの効果を確認するには、`CRecordset`オブジェクト。 これらのメンバー関数が返す、Microsoft Access 7.0 の ODBC ドライバーの`SQL_CB_CLOSE`Access ドライバーがカーソル位置の保持をサポートしていないためです。 そのため、呼び出す必要がある`CRecordset::Requery`次、`CommitTrans`または`Rollback`操作。

複数のトランザクションを 1 つずつ実行する必要がある場合を呼び出すことはできません`Requery`後、最初のトランザクションと次の 1 つを開始します。 [次へ] 呼び出しの前に、レコード セットを閉じる必要があります`BeginTrans`Jet の要件を満たすためにします。 このテクニカル ノートには、このような状況を処理する 2 つの方法について説明します。

- それぞれの後、レコード セットを閉じる`CommitTrans`または`Rollback`操作。

- ODBC API 関数を使用して`SQLFreeStmt`します。

## <a name="closing-the-recordset-after-each-committrans-or-rollback-operation"></a>各 CommitTrans またはロールバック操作の後に、レコード セットを閉じる

トランザクションを開始する前に、レコード セット オブジェクトが閉じられていることを確認します。 呼び出した後`BeginTrans`を呼び出して、レコード セットの`Open`メンバー関数。 レコード セットを呼び出した後すぐに閉じる`CommitTrans`または`Rollback`します。 繰り返しレコード セットの開閉がアプリケーションのパフォーマンスを低下することに注意してください。

## <a name="using-sqlfreestmt"></a>SQLFreeStmt の使用

ODBC API 関数を使用することもできます。`SQLFreeStmt`を明示的にトランザクションを終了した後、カーソルを閉じます。 別のトランザクションを開始するには、呼び出す`BeginTrans`続けて`CRecordset::Requery`します。 呼び出すときに`SQLFreeStmt`、レコード セットの HSTMT は最初のパラメーターとして指定する必要がありますと*SQL_CLOSE* 2 番目のパラメーター。 このメソッドが終了し、すべてのトランザクションの先頭のレコード セットを開くよりも高速です。 次のコードでは、この手法を実装する方法を示します。

```cpp
CMyDatabase db;
db.Open("MYDATASOURCE");
CMyRecordset rs(&db);

// start transaction 1 and
// open the recordset
db.BeginTrans();
rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans(); // or Rollback()

// close the cursor
::SQLFreeStmt(rs.m_hstmt, SQL_CLOSE);

// start transaction 2
db.BeginTrans();
// now get the result set
rs.Requery();

// manipulate data

// end transaction 2
db.CommitTrans();

rs.Close();
db.Close();
```

この手法を実装する別の方法は、新しい関数を記述する`RequeryWithBeginTrans`、1 つ目のロールバックまたはコミットした後、[次へ] のトランザクションの開始を呼び出すことができます。 このような関数を記述するには、次の手順を実行します。

1. コードをコピーし`CRecordset::Requery( )`新しい関数をします。

2. 次の行を追加する呼び出しのすぐ後`SQLFreeStmt`:

   `m_pDatabase->BeginTrans( );`

これでトランザクションの各ペアの間には、この関数を呼び出すことができます。

```cpp
// start transaction 1 and
// open the recordset
db.BeginTrans();

rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans();   // or Rollback()

// close the cursor, start new transaction,
// and get the result set
rs.RequeryWithBeginTrans();

// manipulate data

// end transaction 2
db.CommitTrans();   // or Rollback()
```

> [!NOTE]
> レコード セットのメンバー変数を変更する必要がある場合は、この手法を使用しないでください*か*または*レコード*トランザクション間で。 その場合は、それぞれの後、レコード セットを閉じる必要があります`CommitTrans`または`Rollback`操作。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
