---
title: データ ソースへの接続
ms.date: 11/04/2016
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
ms.openlocfilehash: 1740a34036798dac69ffc8b486e03bf6439845a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395990"
---
# <a name="connecting-to-a-data-source"></a>データ ソースへの接続

ODBC データ ソースは、特定のデータ、データ、およびデータ ソース名を使用して記述されるデータ ソースの場所にアクセスするために必要な情報セットです。 プログラムの観点から、データ、DBMS、(ある場合) は、ネットワーク、および ODBC データ ソースが含まれます。

データ ソースによって提供されるデータにアクセスするには、プログラムはまず、データ ソースに接続を確立する必要があります。 すべてのデータ アクセスは、その接続を介して管理されます。

データ ソースへの接続がクラスによってカプセル化された[CDatabase](../../mfc/reference/cdatabase-class.md)します。 ときに、`CDatabase`オブジェクトがデータ ソースに接続されていることができます。

- 構築[レコード セット](../../mfc/reference/crecordset-class.md)レコードのテーブルまたはクエリを選択します。

- 管理[トランザクション](../../data/odbc/transaction-odbc.md)、バッチ処理の更新すべてがデータ ソースにコミットを一度に (またはデータ ソースは変更されません、バックアップ全体のトランザクションはロールバックされます): データ ソースが必要なレベルのトランザクションをサポートしている場合。

- 直接実行[SQL](../../data/odbc/sql.md)ステートメント。

データ ソース接続の操作が完了したら、閉じる、`CDatabase`オブジェクトとそれを破棄するか、新しい接続の再利用します。 データ ソース接続の詳細については、次を参照してください。[データ ソース (ODBC)](../../data/odbc/data-source-odbc.md)します。

## <a name="see-also"></a>関連項目

[ODBC と MFC](../../data/odbc/odbc-and-mfc.md)