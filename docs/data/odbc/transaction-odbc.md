---
title: トランザクション (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
ms.openlocfilehash: a151ec5ca2b4bdc19bfa7dc626aebda0740a2c9e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329921"
---
# <a name="transaction-odbc"></a>トランザクション (ODBC)

このトピックの内容は、MFC ODBC クラスに該当します。

トランザクションは、グループ、または一連の更新をバッチ処理する方法、[データソース](../../data/odbc/data-source-odbc.md)すべてが一度にコミットされるかは、トランザクションをロールバックするようにします。 トランザクションを使用しない場合、データ ソースへの変更は、オンデマンドでコミットされるのではなく、自動的にコミットされます。

> [!NOTE]
>  すべての ODBC データベース ドライバーでは、トランザクションをサポートします。 呼び出す、`CanTransact`のメンバー関数、 [CDatabase](../../mfc/reference/cdatabase-class.md)または[CRecordset](../../mfc/reference/crecordset-class.md)ドライバーが特定のデータベースのトランザクションをサポートしているかどうかを判断するオブジェクト。 なお`CanTransact`はわかりませんかどうか、データ ソースが完全なトランザクションのサポートを提供します。 呼び出す必要がある`CDatabase::GetCursorCommitBehavior`と`CDatabase::GetCursorRollbackBehavior`後`CommitTrans`と`Rollback`開くときに、トランザクションの影響を確認`CRecordset`オブジェクト。

呼び出し、`AddNew`と`Edit`のメンバー関数は、`CRecordset`オブジェクトのデータ ソースを呼び出すとすぐに影響`Update`します。 `Delete` 呼び出しもすぐに反映します。 複数の呼び出しで構成されるトランザクションを使用する一方、 `AddNew`、 `Edit`、 `Update`、および`Delete`、これは実行しますが、呼び出すまで、コミットされていない`CommitTrans`明示的にします。 トランザクションを確立するには、それらをロールバックする機能を維持しながら、一連のような呼び出しを実行できます。 重要なリソースが利用できない、またはその他のいくつかの条件により、全体のトランザクションの完了、することができます、トランザクション ロールバック、そのコミットではなく。 その場合は、データ ソースのどのトランザクションに属する変更に影響します。

> [!NOTE]
>  現時点では、クラス`CRecordset`バルク行フェッチを実装している場合は、データ ソースへの更新をサポートしません。 つまりへの呼び出しを行うことはできません`AddNew`、 `Edit`、 `Delete`、または`Update`します。 ただし、ことに、更新プログラムを実行し、特定のトランザクション内でこれらの関数を呼び出す独自の関数を作成できます。 バルク行フェッチの詳細については、次を参照してください。[レコード セット。(ODBC) バルク行フェッチ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)します。

> [!NOTE]
>  トランザクションの ODBC を使用する限り、直接実行する SQL ステートメントの影響だけでなく、レコード セットに影響を与える、 **HDBC**に関連付けられている、`CDatabase`オブジェクトまたは ODBC **HSTMT**に基づいて**HDBC**します。

トランザクションは、複数のレコードが同時に更新する必要がある場合に特に便利です。 この場合、最後の更新が行われる前に例外がスローされた場合に発生する可能性がありますなど半分完了したトランザクションを回避します。 このような更新プログラムをトランザクションにグループ化と、変更からの回復 (ロールバック) でき、状態に戻すレコードを返します。 たとえば、銀行では、アカウント A から B のアカウントへのお金を転送場合、両方は、資金を正しく処理する、引き出しが A、預金から B が成功する必要がありますか、トランザクション全体が失敗する必要があります。

データベース クラスで使用したトランザクションを実行して`CDatabase`オブジェクト。 A`CDatabase`オブジェクトが、データ ソースへの接続を表し、1 つまたは複数のレコード セットが関連付けられた`CDatabase`オブジェクトは、レコード セットのメンバー関数を使用して、データベースのテーブルを操作します。

> [!NOTE]
>  トランザクションの 1 つだけのレベルがサポートされています。 トランザクションを入れ子にすることはできません。 また、トランザクションが複数のデータベース オブジェクトにまたがることができます。

トランザクションの実行方法の詳細については、以下のトピックです。

- [トランザクション: レコードセットでのトランザクションの実行 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [トランザクション: トランザクションが更新処理に与える影響 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>関連項目

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)