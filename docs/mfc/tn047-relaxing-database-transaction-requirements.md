---
title: TN047:データベース トランザクション要件の緩和
ms.date: 11/04/2016
f1_keywords:
- vc.data
helpviewer_keywords:
- TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
ms.openlocfilehash: 968420658a90c983d8e6c3eaf1e0c61603fc5441
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305347"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047:データベース トランザクション要件の緩和

MFC ODBC データベース クラスのトランザクション要件のように、このテクニカル ノートでは廃止されました。 データベース クラスがカーソルをレコード セットの後に保持されることを必須 MFC 4.2 では、前に、 **CommitTrans**または**ロールバック**操作。 ODBC ドライバーと DBMS がこのレベルのカーソル位置の保持をサポートしていない場合、データベース クラスは、有効にしていないトランザクション。

データベース クラスは、MFC の 4.2 以降では、カーソル位置の保持を要求する場合の制限を緩和しました。 ドライバーはそれらをサポートしている場合は、トランザクションを有効になります。 、の効果が今すぐ確認する必要があります、 **CommitTrans**または**ロールバック**オープンのレコード セットで操作します。 メンバー関数を参照してください。 [CDatabase::GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior)と[CDatabase::GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior)詳細についてはします。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
