---
title: 既定の処理の変更 (MFC データ アクセス)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
ms.openlocfilehash: fc448ae1e13025a83b33386c2845bdf7bb4d5eec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398023"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>既定の処理の変更 (MFC データ アクセス)

[MFC アプリケーション ウィザード](../mfc/reference/database-support-mfc-application-wizard.md)が 1 つのテーブルのすべてのレコードを選択したレコード セット クラスを書き込みます。 この動作は多くの場合、次の 1 つ以上の方法で変更する必要があります。

- レコードセットのフィルターまたは並べ替え順序の設定。 これを行う`OnInitialUpdate`recordset オブジェクトを構築する前にその`Open`メンバー関数が呼び出されます。 詳細については、次を参照してください。[レコード セット。レコード (ODBC) のフィルター処理](../data/odbc/recordset-filtering-records-odbc.md)と[レコード セット。レコードの並べ替え (ODBC)](../data/odbc/recordset-sorting-records-odbc.md)します。

- レコードセットのパラメーター化。 実際のランタイム パラメーター値はフィルターの後に指定します。 詳細については、次を参照してください。[レコード セット。レコードセットのパラメーター化 (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

- カスタマイズされた SQL 文字列を渡す、[オープン](../mfc/reference/crecordset-class.md#open)メンバー関数。 この手法で行うことができますの詳細については、次を参照してください[SQL:。レコード セットの SQL ステートメント (ODBC) のカスタマイズ](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)します。

## <a name="see-also"></a>関連項目

[レコード ビューの使用](../data/using-a-record-view-mfc-data-access.md)