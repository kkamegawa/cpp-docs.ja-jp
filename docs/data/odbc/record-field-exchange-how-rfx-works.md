---
title: レコード フィールド エクス チェンジ:RFX のしくみ
ms.date: 11/04/2016
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
ms.openlocfilehash: 7da9d480f16dcb6bc5ded0a1dff559b1b1ac4b38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395704"
---
# <a name="record-field-exchange-how-rfx-works"></a>レコード フィールド エクス チェンジ:RFX のしくみ

このトピックでは、RFX プロセスについて説明します。 これは、高度なトピック。

- [RFX とレコード セット](#_core_rfx_and_the_recordset)

- [RFX プロセス](#_core_the_record_field_exchange_process)

> [!NOTE]
>  このトピックの対象から派生したクラス`CRecordset`バルク行フェッチは実装されていません。 バルク行フェッチを使用している場合は、バルク レコード フィールド エクス チェンジ (Bulk RFX) が実装されます。 バルク rfx 関数は、rfx 関数に似ています。 相違点を理解するのを参照してください。[レコード セット。(ODBC) バルク行フェッチ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)します。

##  <a name="_core_rfx_and_the_recordset"></a> RFX とレコード セット

これらをまとめるには、レコード セット オブジェクトのフィールド データ メンバーは、選択した列の 1 つのレコードを保持するエディット バッファーを構成します。 レコード セットを最初に開くし、最初のレコードを読み取るには、ときに結び付けられます) 各は、適切なフィールド データ メンバーのアドレスに列を選択します。 RFX が SQL を送信する ODBC API 関数を呼び出し、レコード セットは、レコードを更新、ときに**UPDATE**または**挿入**ドライバーにステートメント。 RFX では、フィールド データ メンバーのナレッジを使用して、記述する列を指定します。

フレームワークでは特定の段階でエディット バッファーをバックアップに必要な場合、その内容を復元できるようにします。 Rfx 関数は、新しいレコードを追加する前に、既存のレコードを編集する前に、エディット バッファーをバックアップします。 場合によっては、たとえば、エディット バッファーが復元後に、`Update`呼び出し次`AddNew`します。 破棄した場合、新しく変更した編集バッファーなどを呼び出す前に別のレコードに移動、編集のバッファーは復元されません`Update`します。

データ ソースとレコード セットのフィールド データ メンバーの間でデータを交換するだけでなくは、rfx 関数は、バインド パラメーターを管理します。 順序で、パラメーター データ メンバーがバインドされているレコード セットが開かれたときに、"?"SQL ステートメント内のプレース ホルダーを`CRecordset::Open`を構築します。 詳細については、次を参照してください。[レコード セット。レコード セット (ODBC) をパラメーター化](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)します。

レコード セット クラスのオーバーライド`DoFieldExchange`双方向のデータの移動、すべての作業です。 ダイアログ データ エクス チェンジ (DDX) などは、RFX には、クラスのデータ メンバーに関する情報が必要があります。 ウィザードのレコード セットに固有の実装を記述することで、必要な情報を提供する`DoFieldExchange`フィールドのデータに基づいて、ウィザードで指定したメンバーの名前とデータ型。

##  <a name="_core_the_record_field_exchange_process"></a> レコード フィールド交換プロセス

このセクションは、レコード セット オブジェクトが開かれると、RFX イベントのシーケンスをについて説明し、追加すると、更新、およびレコードを削除します。 テーブル[レコード セットを開くときの RFX 操作のシーケンス](#_core_sequence_of_rfx_operations_during_recordset_open)とテーブル[スクロール時の RFX 操作のシーケンス](#_core_sequence_of_rfx_operations_during_scrolling)このトピックでは、RFX プロセスとしての処理を示して、`Move`コマンド、レコード セットと更新します。 これらのプロセス中に[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)が呼び出され、多くのさまざまな操作を実行します。 `m_nOperation`のデータ メンバー、 [CFieldExchange](../../mfc/reference/cfieldexchange-class.md)オブジェクトが必要な操作を決定します。 役に立つことを読み取る[レコード セット。レコード選択による (ODBC) の記録](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)と[レコード セット。どのレコードの更新 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)このマテリアルを読む前にします。

###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a> RFX:列とパラメーターの最初のバインド

次の RFX アクティビティが発生したレコード セット オブジェクトを呼び出すと、表示順序[オープン](../../mfc/reference/crecordset-class.md#open)メンバー関数。

- レコード セットにパラメーター データ メンバーがある場合、フレームワーク`DoFieldExchange`レコード セットの SQL ステートメントの文字列のパラメーター プレース ホルダーにパラメーターをバインドします。 各プレース ホルダーのパラメーターの値の型に依存する表現が使用されるデータがある、**選択**ステートメント。 これは、SQL ステートメントの準備ができたらが実行される前に発生します。 ステートメントの準備については、次を参照してください。、`::SQLPrepare`関数、ODBC の*プログラマーズ リファレンス*します。

- Framework 呼び出し`DoFieldExchange`をもう一度、レコード セット内の対応するフィールド データ メンバーを選択した列の値をバインドします。 これにより、レコード セット オブジェクトが最初のレコードの列を含むをエディット バッファーとして確立されます。

- レコード セットは、SQL ステートメントを実行し、データ ソースが最初のレコードを選択します。 レコード セットのフィールド データ メンバーには、レコードの列が読み込まれます。

次の表は、レコード セットを開くときに、RFX 操作のシーケンスを示します。

### <a name="_core_sequence_of_rfx_operations_during_recordset_open"></a> レコード セットの開始中に RFX 処理の流れ

|操作|DoFieldExchange 操作|データベースと SQL の操作|
|--------------------|-------------------------------|-----------------------------|
|1.レコード セットを開きます。|||
||2.SQL ステートメントを作成します。||
|||3.SQL を送信します。|
||4.パラメーターのデータ メンバーにバインドします。||
||5.フィールド データ メンバーは、列にバインドします。||
|||6.ODBC は、移動を行い、データを設定します。|
||7.C++ 用のデータを修正します。||

レコード セットでは、ODBC の準備の実行を使用して、同じ SQL ステートメントを使用して高速なクエリを再実行できるようにします。 準備実行の詳細については、ODBC SDK を参照してください。*プログラマーズ リファレンス*、MSDN ライブラリ。

###  <a name="_mfc_rfx.3a_.scrolling"></a> RFX:スクロール

1 つのレコードから別にスクロールするときに、フレームワーク`DoFieldExchange`以前新しいレコードの値を持つフィールド データ メンバーに格納されている値を置き換えます。

次の表は、ユーザーがレコード間を移動すると、RFX 操作のシーケンスを示します。

### <a name="_core_sequence_of_rfx_operations_during_scrolling"></a> スクロール中に RFX 処理の流れ

|操作|DoFieldExchange 操作|データベースと SQL の操作|
|--------------------|-------------------------------|-----------------------------|
|1.呼び出す`MoveNext`またはその他の移動機能の 1 つ。|||
|||2.ODBC は、移動を行い、データを設定します。|
||3.C++ 用のデータを修正します。||

###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a> RFX:新しいレコードを追加して、既存のレコードの編集

新しいレコードを追加する場合、レコード セットは、新しいレコードの内容をビルドするをエディット バッファーとして動作します。 レコードを追加する場合と同様のレコードの編集は、レコード セットのフィールド データ メンバーの値の変更が伴います。 RFX の観点から、シーケンスのとおりです。

1. レコード セットの呼び出し[AddNew](../../mfc/reference/crecordset-class.md#addnew)または[編集](../../mfc/reference/crecordset-class.md#edit)と、後で復元できるように、現在の編集のバッファーを格納する rfx 関数のメンバー関数。

1. `AddNew` または`Edit`RFX が変更されたフィールド データ メンバーを検出できるように編集バッファー内のフィールドを準備します。

   新しいレコードに使用すると、新しいものを比較する前の値があるないため`AddNew`PSEUDO_ 値に各フィールド データ メンバーの値を設定します。 後で、呼び出すときに`Update`、RFX PSEUDO_ 値を持つ各データ メンバーの値を比較します。 違いがある場合、データ メンバーが設定されています。 (PSEUDO_ はレコードの列に Null 値を true と同じがこれらのいずれかと同じC++NULL です)。

   異なり、`Update`に対して呼び出す`AddNew`、`Update`に対して呼び出す`Edit`PSEUDO_ を使用するのではなく、以前に格納された値で更新された値を比較します。 その違いは`AddNew`比較の以前に格納された値がありません。

1. 直接を編集する値を持つか、新しいレコードを入力することは、フィールド データ メンバーの値を設定します。 これは、呼び出しを含めることができます`SetFieldNull`します。

1. 呼び出し[Update](../../mfc/reference/crecordset-class.md#update)手順 2. で説明されている、変更されたフィールド データ メンバーを確認します (表を参照して[スクロール時の RFX 操作のシーケンス](#_core_sequence_of_rfx_operations_during_scrolling))。 [なし] が変更された場合`Update`0 を返します。 一部のフィールド データ メンバーが変更された場合`Update`準備して、SQL を実行します。**挿入**レコード内のすべての更新されたフィールドの値を含むステートメント。

1. `AddNew`、`Update`前に、の現在のレコードの以前に格納された値を復元することによって最後に、`AddNew`呼び出します。 `Edit`で、編集後の新しい値を保持します。

次の表は、新しいレコードを追加または既存のレコードを編集するときに、RFX 操作のシーケンスを示します。

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>AddNew および編集時に RFX 処理の流れ

|操作|DoFieldExchange 操作|データベースと SQL の操作|
|--------------------|-------------------------------|-----------------------------|
|1.呼び出す`AddNew`または`Edit`します。|||
||2.エディット バッファーをバックアップします。||
||3.`AddNew`、フィールド データ メンバーを「クリーン」としてマーク、および Null です。||
|4.レコード セットのフィールド データ メンバーに値を割り当てます。|||
|5.`Update` を呼び出す。|||
||6.変更されたフィールドを確認します。||
||7.SQL をビルド**挿入**ステートメント`AddNew`または**更新**ステートメント`Edit`。||
|||8.SQL を送信します。|
||9.`AddNew`、そのバックアップの内容をエディット バッファーを復元します。 `Edit`バックアップを削除します。||

### <a name="rfx-deleting-existing-records"></a>RFX:既存のレコードを削除します。

レコードを削除するときに RFX モジュールによって、レコードが削除されたことをオフに移動する必要がありますを知らせるリマインダーとして、すべてのフィールドが NULL に設定します。 その他の RFX シーケンス情報が不要です。

## <a name="see-also"></a>関連項目

[レコード フィールド エクスチェンジ (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[MFC ODBC コンシューマーします。](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[マクロ、グローバル関数、およびグローバル変数](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange クラス](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)