---
title: ダイナセットを使う場合の ODBC ドライバーの必要条件
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
ms.openlocfilehash: c44e34023ecdeb994ea3a60ea3b699cd5b1488a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395756"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>ダイナセットを使う場合の ODBC ドライバーの必要条件

ダイナセットでは、MFC ODBC データベース クラスで、動的プロパティを持つレコード セットです。特定の方法でデータ ソースと同期されたままになります。 MFC ダイナセットを使う場合 (ただし、前方スクロール専用レコード セット) でレベル 2 API 準拠 ODBC ドライバーが必要です。 場合のドライバー、[データソース](../../data/odbc/data-source-odbc.md)レベル 1 の API に準拠している設定すると、引き続き使用できますが、更新可能なと読み取り専用のスナップショットと順方向専用のレコード セット ダイナセットは。 ただし、拡張のフェッチとキーセット ドリブン カーソルをサポートしている場合は、レベル 1 のドライバーはダイナセットを使う場合をサポートできます。

ODBC の用語でダイナセットを使う場合とスナップショットと呼びますカーソル。 カーソルは、レコード セット内の位置を追跡するために使用されるメカニズムです。 ダイナセットを使う場合のドライバーの要件の詳細については、次を参照してください。[ダイナセット](../../data/odbc/dynaset.md)します。 カーソルの詳細については、次を参照してください。、[オープン データベース コネクティビティ (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) MSDN ドキュメント内の SDK です。

> [!NOTE]
>  更新可能なレコード セットの場合、ODBC ドライバーが位置指定の update ステートメントのいずれかをサポートする必要がありますまたは`::SQLSetPos`ODBC API 関数。 MFC を使用して、両方がサポートされている場合`::SQLSetPos`効率が向上します。 また、スナップショットの場合は、更新可能なスナップショット (静的カーソルと位置指定の update ステートメント) に必要なサポートを提供するカーソル ライブラリを使用できます。

## <a name="see-also"></a>関連項目

[ODBC の基礎](../../data/odbc/odbc-basics.md)