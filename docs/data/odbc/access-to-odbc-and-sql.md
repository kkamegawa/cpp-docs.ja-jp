---
title: ODBC や SQL へのアクセス
ms.date: 11/04/2016
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
ms.openlocfilehash: 7a539d911bbf4f4d9582da0ebedaeffaa0d8fa7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396003"
---
# <a name="access-to-odbc-and-sql"></a>ODBC や SQL へのアクセス

Microsoft Foundation Class ライブラリでは、Windows API 呼び出しの多くをカプセル化し、まだする任意の Windows API 関数を直接呼び出すことができます。 データベース クラスでは、ODBC API に関して同様の柔軟性を提供します。 データベース クラスをシールドすると、ODBC の複雑さの多くが、中には、任意の場所から直接 ODBC API 関数を呼び出すことができます、プログラムでします。

同様に、データベース クラスからも保護では多くの作業をしなくて[SQL](../../data/odbc/sql.md)、する場合は SQL を直接使用することができます。 レコード セット オブジェクトをカスタマイズするには、カスタムの SQL ステートメント (または既定のステートメントの一部を設定) を渡すことによって、レコード セットを開くとします。 使用して直接 SQL 呼び出しを行うことができます、 [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)クラスのメンバー関数[CDatabase](../../mfc/reference/cdatabase-class.md)します。

詳細については、次を参照してください[ODBC:。呼び出し元の ODBC API 関数を直接](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)と[SQL:SQL の直接呼び出し (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)します。

## <a name="see-also"></a>関連項目

[ODBC と MFC](../../data/odbc/odbc-and-mfc.md)