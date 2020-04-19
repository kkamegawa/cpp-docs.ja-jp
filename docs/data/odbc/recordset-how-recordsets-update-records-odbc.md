---
title: レコード セット:レコード セットの更新が (ODBC) を記録する方法
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
ms.openlocfilehash: bf71f562714e2dacfe75540e1e532219b3eb307f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397810"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>レコード セット:レコード セットの更新が (ODBC) を記録する方法

このトピックの内容は、MFC ODBC クラスに該当します。

能力をデータ ソースからレコードを選択するだけでなくレコード セット (必要に応じて) を更新または選択したレコードを削除したり新しいレコードを追加できます。 3 つの要素は、レコード セットの更新を決定します。 接続されたデータ ソースが更新可能かどうか、レコード セット オブジェクトでは、および作成される SQL を作成するときに指定するオプション。

> [!NOTE]
>  SQL、`CRecordset`オブジェクトをベース レコード セットの更新に影響を与えることができます。 たとえば、SQL には、結合が含まれている場合、 **GROUP BY**を FALSE に句では、MFC の設定の更新。

> [!NOTE]
>  このトピックの内容は、バルク行フェッチが実装されていない `CRecordset` の派生オブジェクトを対象にしています。 バルク行フェッチを使用している場合は、次を参照してください。[レコード セット。(ODBC) バルク行フェッチ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)します。

このトピックでは、次の内容について説明します。

- [レコード セットを更新](#_core_your_role_in_recordset_updating)と、フレームワークが何をします。

- [レコード セットをエディット バッファーとして](#_core_the_edit_buffer)と[ダイナセットを使う場合とスナップショットの相違点](#_core_dynasets_and_snapshots)します。

[レコードセット: どの AddNew、Edit、および作業の削除 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)レコード セットの観点からこれらの関数の動作について説明します。

[レコードセット: 詳細についての更新 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)レコード セットの更新プログラムのストーリーを完了するには、トランザクションが更新プログラムに与える影響、レコード セットを閉じるか、またはスクロールが進行中の更新プログラムに影響し、更新プログラムが他のユーザーの更新プログラムとやり取りする方法を説明します。

##  <a name="_core_your_role_in_recordset_updating"></a> レコード セットを更新

次の表では、追加、編集、またはフレームワークの動作をすると、レコードを削除するレコード セットを使用して、ロールを示します。

### <a name="recordset-updating-you-and-the-framework"></a>レコード セットを更新しています。フレームワーク

|プログラマの役割|フレームワークの役割|
|---------|-------------------|
|データ ソースが更新可能な (または追加可能) であるかどうかを確認します。|提供[CDatabase](../../mfc/reference/cdatabase-class.md)データ ソースの更新または追加をテストするためのメンバー関数。|
|(任意の型) の更新可能なレコード セットを開きます。||
|呼び出すことによって、レコード セットは更新可能かどうかを判断`CRecordset`などの関数を更新`CanUpdate`または`CanAppend`します。||
|レコード セットの追加、編集、およびレコードを削除するメンバー関数を呼び出します。|レコード セット オブジェクトとデータ ソース間でデータを交換するためのメカニズムを管理します。|
|必要に応じて、更新プロセスを制御するのにトランザクションを使用します。|提供`CDatabase`トランザクションをサポートするメンバー関数。|

トランザクションの詳細については、次を参照してください。[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)します。

##  <a name="_core_the_edit_buffer"></a> エディット バッファー

まとめて実行されると、レコード セットのフィールド データ メンバーを 1 つのレコードを含むをエディット バッファーとして機能、現在のレコード。 更新操作では、このバッファーを使用して、現在のレコードで処理します。

- レコードを追加するときに、エディット バッファーは、新しいレコードを作成に使用されます。 レコードの追加が完了したら、以前の現在のレコードが再び現在。

- 更新するときに、レコード セットのフィールド データ メンバーを新しい値に設定する (編集)、編集、レコードのバッファーが使用されます。 更新が完了したら、更新されたレコードがまだ最新です。

呼び出すと[AddNew](../../mfc/reference/crecordset-class.md#addnew)または[編集](../../mfc/reference/crecordset-class.md#edit)、必要に応じて、後で復元できるように、現在のレコードが格納されます。 呼び出すと[削除](../../mfc/reference/crecordset-class.md#delete)別のレコードをスクロールする必要があります、および現在のレコードが保存されず、削除済みとしてマークされます。

> [!NOTE]
>  エディット バッファーは、レコードの削除の役割を果たしますありません。 現在のレコードを削除して、レコードは、削除済みとしてマークされている別のレコードをスクロールするまでに、"レコード"ではなく、レコード セットが。

##  <a name="_core_dynasets_and_snapshots"></a> ダイナセットを使う場合とスナップショット

[ダイナセットを使う場合](../../data/odbc/dynaset.md)レコードをスクロールすると、レコードの内容を更新します。 [スナップショット](../../data/odbc/snapshot.md)を呼び出さない限り、レコードの内容が更新されないため、レコードの静的な表現を[Requery](../../mfc/reference/crecordset-class.md#requery)します。 ダイナセットを使う場合のすべての機能を使用するには、ODBC API のサポートの適切なレベルに準拠している ODBC ドライバーで作業する必要があります。 詳細については、次を参照してください。 [ODBC](../../data/odbc/odbc-basics.md)と[ダイナセット](../../data/odbc/dynaset.md)します。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: AddNew、Edit、Delete の動作のしくみ (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)