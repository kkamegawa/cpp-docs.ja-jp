---
title: TN045:Long Varchar、Varbinary の MFC データベース サポート
ms.date: 11/04/2016
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
ms.openlocfilehash: 3e8b356027e5c5b7c604a0354624d9f11e32fb9a
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611058"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045:MFC/データベースの Long のサポート

> [!NOTE]
>  次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

このメモを取得し、ODBC を送信する方法を説明します。 **SQL_LONGVARCHAR**と**SQL_LONGVARBINARY**データベース クラスのデータ型が、MFC を使用します。

## <a name="overview-of-long-varcharvarbinary-support"></a>Long Varchar/Varbinary サポートの概要

ODBC **SQL_LONG_VARCHAR**と**SQL_LONGBINARY** (ここで時間の長いデータ列と呼ぶ) データ型は、膨大な量のデータを保持できます。 このデータを処理できる 3 つの方法があります。

- バインドする`CString` /`CByteArray`します。

- バインドする`CLongBinary`します。

- しないまったくバインドし取得ようにし、長い形式のデータ値を手動で送信、データベース クラスに依存しません。

3 つのメソッドのそれぞれは、長所と短所にあります。

長い形式のデータ列がクエリにパラメーターはサポートされていません。 OutputColumns にのみサポートされます。

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>CString/CByteArray への長い形式のデータ列のバインド

利点:

この方法はわかりやすくと使い慣れたクラスを使用します。 フレームワークを提供`CFormView`サポート`CString`で`DDX_Text`します。 文字列またはコレクションの一般的な機能の多くがある、`CString`と`CByteArray`クラス、およびするには、データ値を保持するには、ローカルで割り当てられたメモリの量を制御できます。 フレームワークが古い中にフィールドのデータのコピーを保持`Edit`または`AddNew`関数呼び出し、およびデータへの変更を自動的に検出フレームワークのことができます。

> [!NOTE]
>  `CString` 、文字データを操作するために設計されていますが、`CByteArray`バイナリ データで作業をお勧め文字データを配置すること (**SQL_LONGVARCHAR**) に`CString`、およびバイナリ データ (**SQL_LONGVARBINARY**) に`CByteArray`します。

RFX 関数の`CString`と`CByteArray`追加の引数があるデータの列を取得した値を保持するために割り当てられたメモリの既定のサイズをオーバーライドすることができます。 次の関数宣言で格納引数に注意してください。

```
void AFXAPI RFX_Text(CFieldExchange* pFX,
    const char *szName,
    CString& value,
    int nMaxLength = 255,
    int nColumnType =
    SQL_VARCHAR);

void AFXAPI RFX_Binary(CFieldExchange* pFX,
    const char *szName,
    CByteArray& value,
    int nMaxLength = 255);
```

長い形式のデータ列を取得する場合、`CString`または`CByteArray`データの量、既定では、255 バイト、最大値が返されます。 これを超えるものは無視されます。 フレームワークが例外をスローするこの例では、 **AFX_SQL_ERROR_DATA_TRUNCATED**します。 さいわい、増やすことができますに明示的に、大きい値を格納最大**MAXINT**します。

> [!NOTE]
>  MFC でのローカル バッファーを設定する格納の値が使用される、`SQLBindColumn`関数。 これは、データのストレージ用のローカル バッファーであり、ODBC ドライバーによって返されるデータの量を実際には影響しません。 `RFX_Text` `RFX_Binary`のみを使用して呼び出すいずれかを加える`SQLFetch`バック エンド データベースからデータを取得します。 各 ODBC ドライバーでは、1 回のフェッチで返すことも、データの量にさまざまな制限があります。 この制限は、例外の場合で、格納に設定された値よりもはるかに小さい可能性があります**AFX_SQL_ERROR_DATA_TRUNCATED**がスローされます。 このような状況での使用に切り替える`RFX_LongBinary`の代わりに`RFX_Text`または`RFX_Binary`すべてのデータを取得できるようにします。

ClassWizard はバインド、 **SQL_LONGVARCHAR**に、 `CString`、または**SQL_LONGVARBINARY**に、`CByteArray`できます。 255 バイトより大きく、長い形式のデータ列の取得先を割り当てる場合は、格納の明示的な値を指定できます。

長い形式のデータ列のバインド時、`CString`または`CByteArray`、フィールドの更新のしくみを sql _ にバインドされている場合と同じ**VARCHAR**または sql _**VARBINARY**します。 中に`Edit`と後で場合と比較して、データ値をキャッシュ`Update`は、データへの変更は、値し、面倒を設定し、Null 列の値を適切に検出するために呼び出されます。

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>CLongBinary への長い形式のデータ列のバインド

長い形式のデータ列には、詳細を含めることができる場合**MAXINT**バイトのデータには、おそらくを検討してくださいに取得する、`CLongBinary`します。

利点:

これには、最大利用可能なメモリ、全体の長い形式のデータ列を取得します。

欠点:

データは、メモリに保持されます。 このアプローチは非常に大量のデータの負担もあります。 呼び出す必要があります`SetFieldDirty`にバインドされたデータ フィールドを確認するにはメンバーが含まれている、`Update`操作。

長い形式のデータの列を取得する場合、 `CLongBinary`、データベース クラスは、長い形式のデータ列の合計サイズを確認してから割り当てる、`HGLOBAL`データ値全体を保持するのに十分な大きさのメモリ セグメント。 データベース クラスは、割り当てられたに全体のデータ値を取得`HGLOBAL`します。

フレームワークが例外をスロー場合は、データ ソースには、長い形式のデータ列の必要なサイズを返すことはできません、**返せない場合**します。 場合を割り当てようとして、`HGLOBAL`が失敗した、標準的なメモリ例外がスローされます。

ClassWizard はバインド、 **SQL_LONGVARCHAR**または**SQL_LONGVARBINARY**を`CLongBinary`できます。 選択`CLongBinary`としてメンバー変数の追加 ダイアログで、変数の型。 ClassWizard は追加して、`RFX_LongBinary`への呼び出し、`DoFieldExchange`を呼び出すし、バインドされたフィールドの合計数をインクリメントします。

時間の長いデータ列の値を更新するには、最初に確認、割り当てられた`HGLOBAL`呼び出すことによって、新しいデータを保持するために十分な大きさ **:: GlobalSize**上、*により*のメンバー、`CLongBinary`します。 小さすぎる場合、リリース、`HGLOBAL`適切なサイズを 1 つに割り当てるとします。 *ただし*新しいサイズを反映するようにします。

の場合*ただし*サイズよりも大きい、置換するデータのいずれかを解放して再割り当て、 `HGLOBAL`、か、割り当てられたままにします。 実際に使用しているバイト数を示す確認*ただし*します。

## <a name="how-updating-a-clongbinary-works"></a>CLongBinary 動作を更新する方法

理解する必要はありませんが更新する方法、`CLongBinary`動作しますが、これは長い形式のデータ値が、データ ソースに送信する方法の例として利用する可能性があります以下に示すこの 3 つ目のメソッドを選択するかどうか。

> [!NOTE]
>  ために、 `CLongBinary` 、更新プログラムに含まれるフィールドに明示的に呼び出す必要があります`SetFieldDirty`フィールド。 呼び出す必要がある場合は Null に設定を含むフィールドに変更を加えた`SetFieldDirty`します。 呼び出す必要がある`SetFieldNull`、2 番目のパラメーターが**FALSE**値を持つものとしてフィールドにマークします。

更新するときに、`CLongBinary`フィールドでは、データベース クラスを使用して、ODBC の**DATA_AT_EXEC**メカニズム (ODBC のドキュメントを参照して`SQLSetPos`の rgbValue 引数)。 フレームワークが指すのではなく、insert または update ステートメントを準備するときに、 `HGLOBAL` 、データを含む、*アドレス*の`CLongBinary`として設定されて、*値*列の代わりに、長さのインジケーター設定および**SQL_DATA_AT_EXEC**します。 後で、update ステートメントが、データ ソースに送信される`SQLExecDirect`戻ります**SQL_NEED_DATA**します。 これは、アラートは、フレームワークの実際のアドレスにこの列のパラメーターの値が、`CLongBinary`します。 Framework 呼び出し`SQLGetData`1 回、小さなバッファーをデータの実際の長さを返すことを指定してください。 場合は、ドライバーは、バイナリ ラージ オブジェクト (BLOB) の実際の長さを返します、MFC には、BLOB の取得に必要な多くの領域が再割り当ています。 場合は、データ ソースを返します。 **SQL_NO_TOTAL**、BLOB のサイズを特定できないことを示す、MFC は小さなブロックを作成されます。 既定の初期サイズは 64 K、および後続のブロック サイズ 2 倍になります例: 2 つ目は 128 K になります、3 つ目が 256 K、という具合です。 初期サイズは構成できます。

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>バインドされません。SQLGetData と ODBC から直接取得する送信データ

このメソッドを使用する完全にデータベースのクラスをバイパス長い形式のデータ列を処理します。

利点:

動的にどの程度のデータを取得する場合に必要に応じて、ディスク データをキャッシュすることができます。

欠点:

フレームワークのられる`Edit`または`AddNew`サポート、およびするが記述する必要があります自身で基本的な機能を実行するコード (`Delete`が列レベルの操作ではないため、機能)。

この場合、長い形式のデータ列は、レコード セットの選択リストである必要がありますが、フレームワークによってにバインドされていません。 これは実行する 1 つの方法を使用して、独自の SQL ステートメントを指定する`GetDefaultSQL`または lpszSQL の引数として`CRecordset`の`Open`関数とでは余分な列をバインドできません。 ODBC では、バインドされていないフィールドがバインドされたフィールドの右側に表示されることが必要です、そのため、選択リストの末尾に、非バインド列または列を追加します。

> [!NOTE]
>  フレームワークによって、長い形式のデータ列がバインドされていないために変更を加える場合は処理されない`CRecordset::Update`呼び出し。 作成し、必要な SQL を送信する必要があります**挿入**と**UPDATE**ステートメント自分でします。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
