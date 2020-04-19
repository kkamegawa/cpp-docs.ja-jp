---
title: レコード フィールド エクス チェンジ:RFX 関数の使い方
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
ms.openlocfilehash: dc717336a5279e7eda1b7c39b19a7c76f9055cd3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395691"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>レコード フィールド エクス チェンジ:RFX 関数の使い方

このトピックの本文を構成する RFX 関数の呼び出しを使用する方法について説明、`DoFieldExchange`をオーバーライドします。

> [!NOTE]
>  このトピックの対象から派生したクラス[CRecordset](../../mfc/reference/crecordset-class.md)バルク行フェッチは実装されていません。 バルク行フェッチを使用している場合は、バルク レコード フィールド エクス チェンジ (Bulk RFX) が実装されます。 バルク rfx 関数は、rfx 関数に似ています。 相違点を理解するのを参照してください。[レコード セット。(ODBC) バルク行フェッチ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)します。

RFX のグローバル関数では、レコード セットのデータ ソースおよびフィールド データ メンバーの列の間でデータを交換します。 レコード セットの内の RFX 関数呼び出しを記述する[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)メンバー関数。 このトピックでは、関数をについて簡単に説明し、どの rfx 関数は、使用可能なデータ型を示します。 [テクニカル ノート 43](../../mfc/tn043-rfx-routines.md)追加のデータ型の RFX 関数を記述する方法について説明します。

##  <a name="_core_rfx_function_syntax"></a> RFX 関数の構文

各 RFX 関数は、3 つのパラメーターを受け取る (およびオプション 4 または 5 番目のパラメーターをかかる)。

- ポインターを[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)オブジェクト。 単に渡すこと、`pFX`にポインターが渡される`DoFieldExchange`します。

- データ ソースに列の名前が表示されます。

- 対応するフィールドのデータ メンバーまたはレコード セット クラスでパラメーターのデータ メンバーの名前。

- (省略可能)で、関数、文字列または配列を転送中の最大長の一部です。 既定値は 255 (バイト単位) が、これを変更したい場合があります。 最大サイズはの最大サイズに基づきます、`CString`オブジェクト- **INT_MAX** (2,147, 483,647) バイト- が、そのサイズの前に、ドライバーの制限が発生可能性があります。

- (省略可能)`RFX_Text`関数、ことがありますパラメーターを使用する 5 番目の列のデータ型を指定します。

詳細については、RFX 関数の下を参照してください。[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)で、*クラス ライブラリ リファレンス*します。 特別なことの例については、パラメーターの使用を参照してください[レコード セット。合計およびその他の集計の計算 (ODBC) を取得する](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)します。

##  <a name="_core_rfx_data_types"></a> RFX データ型

クラス ライブラリには、多くの異なるデータ型をデータ ソースとレコード セットの間で転送するための RFX 関数が用意されています。 データ型での RFX 関数を次に示します。 RFX 関数呼び出しを記述する必要がありますの場合、データ型でこれらの関数から選択します。

|関数|データの種類|
|--------------|---------------|
|`RFX_Bool`|**BOOL**|
|`RFX_Byte`|**BYTE**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**float**|
|`RFX_Int`|**int**|
|`RFX_Long`|**long**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|


詳細については、RFX 関数のドキュメントを参照してください。[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)で、*クラス ライブラリ リファレンス*します。 C++ のデータ型を SQL データ型にマップする方法については、C++ のデータ型にマップ ANSI SQL データ型のテーブルを参照してくださいで[SQL:。SQL と C++ のデータ型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)します。

## <a name="see-also"></a>関連項目

[レコード フィールド エクスチェンジ (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[レコード フィールド エクスチェンジ: RFX の動作のしくみ](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[レコードセット: レコードセットのパラメーター化 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[レコードセット: データ列の動的なバインド (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset クラス](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange クラス](../../mfc/reference/cfieldexchange-class.md)