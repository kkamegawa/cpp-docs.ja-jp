---
title: 出力パラメーター
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
ms.openlocfilehash: 196c50ea62c3e3188b61a3b35a9e2752740c4ad5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62283966"
---
# <a name="output-parameters"></a>出力パラメーター

ストアド プロシージャの呼び出しは、SQL コマンドを実行すると似ています。 主な違いは、ストアド プロシージャが出力パラメーター (または"出力パラメーター") を使用して、戻り値です。

ストアド プロシージャを次のように最初の ' ですか? '戻り値 (電話) と、2 つ目は、'?' (名) の入力パラメーターです。

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }"))
```

パラメーターのマップでは、in、out パラメーターを指定します。

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter
END_PARAM_MAP()
```

アプリケーションでは、ストアド プロシージャから返された出力を処理する必要があります。 さまざまな OLE DB プロバイダーでは、出力パラメーターを返すし、結果の処理中にさまざまなタイミングで戻り値。 などの Microsoft OLE DB provider for SQL Server (SQLOLEDB) は、出力パラメーターを指定しないし、までコードを返す、コンシューマーが取得またはストアド プロシージャによって返される結果セットが取り消されました。 出力は、最後の TDS パケットで、サーバーから返されます。

## <a name="row-count"></a>行数

出力パラメーターを持つストアド プロシージャを実行する OLE DB コンシューマー テンプレートを使用する場合、行の数は、行セットを終了するまでに設定されていません。

たとえば、行セットと、出力パラメーターを使用してストアド プロシージャを考えてみます。

```sql
create procedure sp_test
   @_rowcount integer output
as
   select top 50 * from test
   @_rowcount = @@rowcount
return 0
```

`@_rowcount`出力パラメーターは、テスト テーブルから返された行の数を報告します。 ただし、このストアド プロシージャは、50 行の数を制限します。 たとえば、テストでの 100 行がある場合は、(このコードでは、上位 50 行のみを取得します) ために、行数は 50 になります。 テーブルには、30 行あったのみ、行数が 30 になります。 必ず`Close`または`CloseAll`値をフェッチする前に、出力パラメーターを設定します。

## <a name="see-also"></a>関連項目

[ストアド プロシージャの使用](../../data/oledb/using-stored-procedures.md)