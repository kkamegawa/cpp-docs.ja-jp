---
title: CFieldExchange クラス
ms.date: 11/04/2016
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
helpviewer_keywords:
- CFieldExchange [MFC], IsFieldType
- CFieldExchange [MFC], SetFieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
ms.openlocfilehash: e66b3ed16d4f21d46567c37bfaf7929d32f63b8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346354"
---
# <a name="cfieldexchange-class"></a>CFieldExchange クラス

データベース クラスで使うレコード フィールド エクスチェンジ (RFX) ルーチンとバルク レコード フィールド エクスチェンジ (Bulk RFX) ルーチンをサポートします。

## <a name="syntax"></a>構文

```
class CFieldExchange
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CFieldExchange::IsFieldType](#isfieldtype)|現在の操作がある場合、0 以外の値を返します。 適切な更新されるフィールドの型。|
|[CFieldExchange::SetFieldType](#setfieldtype)|レコード セットのデータ メンバーの種類を指定します: 列またはパラメーター: 次回の呼び出しまで RFX 関数に次のすべての呼び出しによって表される`SetFieldType`します。|

## <a name="remarks"></a>Remarks

`CFieldExchange` 基本クラスはありません。

バルク行フェッチを実装しているカスタム データ型のデータ エクス チェンジ ルーチンを記述する場合は、このクラスを使用してください。それ以外の場合、直接使用しないこのクラス。 バルク RFX データ ソースの現在のレコードの対応するフィールドとレコード セット オブジェクトのフィールド データ メンバーのデータを交換します。

> [!NOTE]
>  Open Database Connectivity (ODBC) クラスではなく、データ アクセス オブジェクト (DAO) クラスを使用している場合は、クラスを使用して[CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md)代わりにします。 詳細については、この記事を参照してください。[概要: データベース プログラミング](../../data/data-access-programming-mfc-atl.md)します。

A`CFieldExchange`コンテキスト情報に必要なレコード フィールド エクス チェンジまたはをバルク レコード フィールド エクス チェンジの配置オブジェクトを提供します。 `CFieldExchange` オブジェクトは、多くの操作、バインド パラメーター、フィールド データ メンバーなど、現在のレコードのフィールドでさまざまなフラグの設定をサポートします。 バルク RFX 操作によって定義された型のレコード セット クラスのデータ メンバーに対して実行される、 **enum** **FieldType**で`CFieldExchange`します。 考えられる**FieldType**値は。

- `CFieldExchange::outputColumn` フィールド データ メンバーにします。

- `CFieldExchange::inputParam` または`CFieldExchange::param`の入力パラメーターのデータ メンバー。

- `CFieldExchange::outputParam` パラメーターのデータ メンバーに出力します。

- `CFieldExchange::inoutParam` 入力/出力パラメーターのデータ メンバーにします。

ほとんどのクラスのメンバー関数とデータ メンバーは、独自のカスタム RFX ルーチンを記述するために提供されます。 使用する`SetFieldType`頻繁にします。 詳細については、記事をご覧ください。[レコード フィールド エクス チェンジ (RFX)](../../data/odbc/record-field-exchange-rfx.md)と[レコード セット (ODBC)](../../data/odbc/recordset-odbc.md)します。 バルク行フェッチの詳細については、この記事を参照してください。[レコード セット。(ODBC) バルク行フェッチ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)します。 グローバル関数とバルク RFX に関する詳細については、次を参照してください。[レコード フィールド エクス チェンジ関数](../../mfc/reference/record-field-exchange-functions.md)この参照の MFC マクロとグローバルのセクションでします。

## <a name="inheritance-hierarchy"></a>継承階層

`CFieldExchange`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdb.h

##  <a name="isfieldtype"></a>  CFieldExchange::IsFieldType

RFX 関数を記述する場合は、呼び出す`IsFieldType`特定フィールドまたはパラメーターのデータ メンバー型に現在の操作を実行できるかどうかを判断する関数の先頭 (、 `CFieldExchange::outputColumn`、 `CFieldExchange::inputParam`、 `CFieldExchange::param`、 `CFieldExchange::outputParam`、または`CFieldExchange::inoutParam`)。

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>パラメーター

*pnField*<br/>
フィールドまたはパラメーターのデータ メンバーの通し番号が、このパラメーターで返されます。 この数は、データ メンバーの順序で、 [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)または[CRecordset::DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)関数。

### <a name="return-value"></a>戻り値

以外の場合、現在のフィールドまたはパラメーターの種類で現在の操作を実行できます。

### <a name="remarks"></a>Remarks

既存の RFX 関数のモデルに従います。

##  <a name="setfieldtype"></a>  CFieldExchange::SetFieldType

呼び出す必要がある`SetFieldType`でレコード セット クラスの[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)または[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)をオーバーライドします。

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>パラメーター

*nFieldType*<br/>
値、`enum FieldType`で宣言された`CFieldExchange`次のいずれかを指定することができます。

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>Remarks

フィールドのデータ メンバーを呼び出す必要がある`SetFieldType`のパラメーターを持つ`CFieldExchange::outputColumn`、rfx 関数または Bulk RFX 関数の呼び出しをその後にします。 バルク行フェッチを実装していないかどうかは、ClassWizard 配置この`SetFieldType`のフィールド マップのセクションでの呼び出し`DoFieldExchange`します。

呼び出す必要がある場合は、レコード セット クラスをパラメーター化する`SetFieldType`、任意のフィールド マップのセクションの外部が続く rfx 関数呼び出しのパラメーターのすべてのデータ メンバーの。 各型のパラメーターのデータ メンバーがいる必要があります独自`SetFieldType`呼び出します。 次の表に、別の値を渡すことができますを区別する`SetFieldType`クラスのパラメーターのデータ メンバーを表す。

|SetFieldType パラメーターの値|パラメーターのデータ メンバーの型|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|入力パラメーターです。 レコード セットのクエリまたはストアド プロシージャに渡される値。|
|`CFieldExchange::param` | 同じ`CFieldExchange::inputParam`します。|
|`CFieldExchange::outputParam`|出力パラメーターです。 レコード セットのストアド プロシージャの戻り値。|
|`CFieldExchange::inoutParam`|入力/出力パラメーターです。 渡されるされ、レコード セットのストアド プロシージャから返される値。|

一般に、フィールド データ メンバーまたはパラメーターのデータ メンバーに関連付けられた RFX 関数の呼び出しの各グループへの呼び出し前が必要`SetFieldType`します。 *NFieldType*の各パラメーター`SetFieldType`呼び出しに続く RFX 関数の呼び出しによって表されるデータ メンバーの種類を識別する、`SetFieldType`呼び出します。

出力および入力/出力パラメーターの処理方法の詳細については、次を参照してください。、`CRecordset`メンバー関数は[FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset)します。 バルク RFX 関数の詳細については、トピックを参照してください。[レコード フィールド エクス チェンジ関数](../../mfc/reference/record-field-exchange-functions.md)します。 バルク行フェッチの詳細については、この記事を参照してください。[レコード セット。(ODBC) バルク行フェッチ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)します。

### <a name="example"></a>例

この例は、RFX 関数の呼び出しを伴ういくつかの呼び出しを示しています。`SetFieldType`します。 なお`SetFieldType`経由で呼び出され、`pFX`へのポインターを`CFieldExchange`オブジェクト。

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[CRecordset クラス](../../mfc/reference/crecordset-class.md)
