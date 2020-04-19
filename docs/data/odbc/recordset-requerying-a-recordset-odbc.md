---
title: レコード セット:クエリの再実行 (Odbc)
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
ms.openlocfilehash: 7edc1c04da617f96165b25a47ce169b266ae0003
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397706"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>レコード セット:クエリの再実行 (Odbc)

このトピックの内容は、MFC ODBC クラスに該当します。

このトピックでは、レコード セット オブジェクトを使用して、クエリを再実行する方法について説明します (つまり、更新) を使用する場合と、データベースから自体、 [Requery](../../mfc/reference/crecordset-class.md#requery)メンバー関数。

クエリの再実行するプリンシパルの理由は次のとおりです。

- ユーザーや他のユーザーによって追加されたレコードとレコード (を削除するものが既に、レコード セット内で反映される) その他のユーザーによって削除されたに関して最新のレコード セットを表示します。

- パラメーター値の変更に基づいて、レコード セットを更新します。

##  <a name="_core_bringing_the_recordset_up_to_date"></a> 日付へのレコード セットの追加

多くの場合、するレコード セット オブジェクトの状態を再クエリする最新の状態。 データベースのマルチ ユーザー環境で他のユーザーを変更できるデータ レコード セットの有効期間中にします。 レコード セットが他のユーザーによって行われた変更を反映するときと、他のユーザーのレコード セットが変更を反映する場合の詳細については、次を参照してください。[レコード セット。レコード セットの更新プログラムによる (ODBC) の記録](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)と[ダイナセット](../../data/odbc/dynaset.md)します。

##  <a name="_core_requerying_based_on_new_parameters"></a> 新しいパラメーターに基づくクエリを再実行

別の頻繁に: と同じくらい重要です-の使用[Requery](../../mfc/reference/crecordset-class.md#requery)は新しい一連のパラメーター値の変更に基づいてレコードを選択します。

> [!TIP]
>  クエリの速度が呼び出した場合に、おそらくはるかに高速`Requery`呼び出した場合よりもパラメーターの値を変更して`Open`もう一度です。

##  <a name="_core_requerying_dynasets_vs.._snapshots"></a> ダイナセットを使う場合とクエリの再実行します。スナップショット

ダイナセットを使う場合は、最新のデータを動的に一連のレコードを提示するものでは、ために、他のユーザーの追加機能を反映する場合に多くの場合、クエリにします。 その一方で、レポートの準備や集計計算などを実行するときに安全にその静的コンテンツに依存することができますので、スナップショットは便利です。 それでも、クエリも、スナップショットを再実行することがあります。 マルチ ユーザー環境では、スナップショット データを他のユーザー データベースの変更がデータ ソースとの同期を失う可能性があります。

#### <a name="to-requery-a-recordset-object"></a>レコード セット オブジェクトを再クエリするには

1. 呼び出す、 [Requery](../../mfc/reference/crecordset-class.md#requery)オブジェクトのメンバー関数。

また、終了して、元のレコード セットを再起動したことができます。 どちらの場合は、新しいレコード セットは、データ ソースの現在の状態を表します。

例については、次を参照してください。[レコード ビュー。2 つ目のレコード セットからリスト ボックス](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)します。

> [!TIP]
>  最適化するために`Requery`、パフォーマンス、レコード セットを変更しないように[フィルター](../../data/odbc/recordset-filtering-records-odbc.md)または[並べ替え](../../data/odbc/recordset-sorting-records-odbc.md)します。 呼び出しの前に、パラメーター値のみを変更する`Requery`します。

場合、`Requery`呼び出しが失敗した呼び出しを再試行することができます。 それ以外の場合、アプリケーションを正常に終了する必要があります。 呼び出し`Requery`または`Open`のさまざまな理由のいずれかが失敗する可能性があります。 おそらく、ネットワーク エラーが発生します。または、呼び出し中に、既存のデータのリリース後、新しいデータを取得すると、前に、別のユーザー可能性があります取得排他的アクセスまたは、レコード セットが依存するテーブルを削除できませんできます。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: データ列の動的なバインド (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[レコードセット: レコードセットの作成成と破棄 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)