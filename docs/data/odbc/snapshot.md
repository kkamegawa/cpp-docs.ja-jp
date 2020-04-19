---
title: スナップショット
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC cursor library [ODBC], snapshots
- cursors [ODBC], static
- recordsets, snapshots
- snapshots, support in ODBC
- static cursors
- ODBC recordsets, snapshots
- cursor library [ODBC], snapshots
- snapshots
ms.assetid: b5293a52-0657-43e9-bd71-fe3785b21c7e
ms.openlocfilehash: 5999f89156d895ff0c87c892be892c6a614a0132
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330038"
---
# <a name="snapshot"></a>スナップショット

スナップショットは、スナップショットの作成時に存在していたデータの静的なビューを反映するレコード セットです。 スナップショットを開くすべてのレコードに移動すると、レコードのセットが含まれます、呼び出すことによって、スナップショットを再構築するまでその値を変更しないで`Requery`します。

> [!NOTE]
>  このトピックの内容は、MFC ODBC クラスに該当します。 MFC ODBC クラスではなく、MFC DAO クラスを使用する場合は、次を参照してください。 [cdaorecordset::open](../../mfc/reference/cdaorecordset-class.md#open)スナップショット タイプのレコード セットの説明についてはします。

更新可能または読み取り専用スナップショットを作成するにはデータベース クラスを使用します。 ダイナセットとは異なり、更新可能なスナップショットが、他のユーザーによって行われた値を記録する変更を反映しませんが、更新と、プログラムによる削除は反映します。 呼び出すまでスナップショットに追加されたレコードは、スナップショットに表示されるならない`Requery`します。

> [!TIP]
>  スナップショットは、ODBC 静的カーソルです。 静的カーソル実際に得られないデータの行まで、そのレコードをスクロールします。 すべてのレコードを直ちに取得するためには、レコード セットの末尾までスクロールし、し、表示する最初のレコードをスクロールできます。 ただし、こと末尾にスクロールためのオーバーヘッドし、パフォーマンスを下げることができます。

スナップショットは、データとレポートの生成または計算を実行するときに、操作中に固定する必要がある場合に最も重要です。 そうであっても、ときどきを再構築するため、スナップショットからデータ ソースは大きく異なることができます。

スナップショットのサポートは、静的カーソルと、位置指定更新は (更新に必要)、任意のレベル 1 のドライバーの ODBC カーソル ライブラリに基づいています。 カーソル ライブラリの DLL は、このサポートのメモリに読み込む必要があります。 構築する際に、`CDatabase`オブジェクトと呼び出しの`OpenEx`メンバー関数を指定する必要がある、`CDatabase::useCursorLib`のオプション、 *dwOptions*パラメーター。 呼び出す場合、`Open`メンバー関数は、カーソル ライブラリは、既定で読み込まれます。 ダイナセットを使う場合のスナップショットではなくを使用している場合、カーソル ライブラリを読み込むをたくないです。

スナップショットは、ときに、ODBC カーソル ライブラリが読み込まれた場合にのみ使用可能な`CDatabase`オブジェクトが構築または使用している ODBC ドライバーは、静的カーソルをサポートしています。

> [!NOTE]
>  一部の ODBC ドライバー (静的カーソル) のスナップショットを更新できません可能性があります。 サポートされるカーソルの種類は、ドライバーのドキュメントとサポートされる同時実行の種類を確認します。 更新可能なスナップショットを確実に作成するときにメモリに、カーソル ライブラリを読み込むことを確認、`CDatabase`オブジェクト。 詳細については、次を参照してください[ODBC:。ODBC カーソル ライブラリ](../../data/odbc/odbc-the-odbc-cursor-library.md)します。

> [!NOTE]
>  2 つの異なるで行う必要がありますスナップショットとダイナセットを使う場合の両方を使用する場合は、`CDatabase`オブジェクト (2 つの接続)。

すべてのレコードのプロパティのスナップショット共有の詳細については、次を参照してください。[レコード セット (ODBC)](../../data/odbc/recordset-odbc.md)します。 ODBC と ODBC カーソル ライブラリを含む、スナップショットの詳細については、次を参照してください。 [ODBC](../../data/odbc/odbc-basics.md)します。

## <a name="see-also"></a>関連項目

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)