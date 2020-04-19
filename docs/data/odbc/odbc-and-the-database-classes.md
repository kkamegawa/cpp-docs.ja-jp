---
title: ODBC とデータベース クラス
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 7692a8128e3dac97c9107e986f6698db76c22c58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395834"
---
# <a name="odbc-and-the-database-classes"></a>ODBC とデータベース クラス

MFC ODBC データベース クラスが通常行う自分でメンバー関数の ODBC API 関数呼び出しをカプセル化、 [CDatabase](../../mfc/reference/cdatabase-class.md)と[CRecordset](../../mfc/reference/crecordset-class.md)クラス。 たとえば、複雑な odbc 呼び出し、返されるレコードには、記憶域の場所、エラーの状態の処理、およびその他の操作のバインディングによって管理されますがデータベース クラス。 その結果、かなり単純なクラス インターフェイスを使用して、レコード セット オブジェクトを使用してレコードを操作します。

> [!NOTE]
>  ODBC データ ソースには、ここで説明するように、MFC ODBC クラス経由でアクセスできます。また、MFC DAO (Data Access Object) クラス経由でもアクセスできます。

データベース クラスには、ODBC の機能がカプセル化が ODBC API 関数の 1 対 1 のマッピングは提供されません。 データベース クラスでは、高いレベルの抽象化、Microsoft Access および Microsoft Visual Basic でのデータ アクセス オブジェクトの検出後にモデル化を提供します。 詳細については、次を参照してください。 [ODBC と MFC](../../data/odbc/odbc-and-mfc.md)します。

## <a name="see-also"></a>関連項目

[ODBC の基礎](../../data/odbc/odbc-basics.md)