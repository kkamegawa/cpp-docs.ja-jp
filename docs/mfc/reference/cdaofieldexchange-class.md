---
title: CDaoFieldExchange クラス
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
ms.openlocfilehash: cfffebd16c3c1d62dc4084b962c22911e4b46ae5
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303884"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange クラス

DAO データベース クラスで使われる DAO レコード フィールド エクスチェンジ (DFX: DAO Record Field eXchange) ルーチンをサポートします。

DAO は Office 2013 でサポートされています。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。

## <a name="syntax"></a>構文

```
class CDaoFieldExchange
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|現在の操作が更新対象のフィールドの型に適している場合は、0以外の値を返します。|
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|次の `SetFieldType`の呼び出しまで、DFX 関数の後続のすべての呼び出しで表される、レコードセットデータメンバー (列またはパラメーター) の種類を指定します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|Name|説明|
|----------|-----------------|
|[CDaoFieldExchange:: m_nOperation](#m_noperation)|レコードセットの `DoFieldExchange` メンバー関数への現在の呼び出しによって実行されている DFX 操作。|
|[CDaoFieldExchange:: m_prs](#m_prs)|DFX 操作が実行されているレコードセットへのポインター。|

## <a name="remarks"></a>コメント

`CDaoFieldExchange` には基底クラスがありません。

カスタムデータ型のデータ交換ルーチンを作成する場合は、このクラスを使用します。それ以外の場合、このクラスは直接使用されません。 DFX は、 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトのフィールドデータメンバーと、データソースの現在のレコードの対応するフィールドとの間でデータを交換します。 DFX は、データソースとデータソースの両方の方向で exchange を管理します。 カスタム DFX ルーチンの記述については、「[テクニカルノート 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) 」を参照してください。

> [!NOTE]
>  DAO データベースクラスは、Open Database Connectivity (ODBC) に基づく MFC データベースクラスとは異なります。 すべての DAO データベースクラス名には、"CDao" プレフィックスが付いています。 DAO クラスを使用して ODBC データソースにアクセスすることもできます。 一般に、DAO に基づく MFC クラスは、ODBC に基づく MFC クラスよりも多くの機能を備えています。 DAO ベースのクラスは、独自のデータベースエンジンを介して、ODBC ドライバーを介してデータにアクセスできます。 また、データ定義言語 (DDL) 操作もサポートされています。これには、自分で DAO を呼び出す必要はなく、クラスを使用したテーブルの追加などがあります。

> [!NOTE]
>  DAO レコードフィールドエクスチェンジ (DFX) は、ODBC ベースの MFC データベースクラス (`CDatabase`、`CRecordset`) のレコードフィールドエクスチェンジ (RFX) によく似ています。 RFX を理解すると、DFX を簡単に使用できることがわかります。

`CDaoFieldExchange` オブジェクトは、DAO レコードフィールドの交換を行うために必要なコンテキスト情報を提供します。 `CDaoFieldExchange` オブジェクトは、パラメーターとフィールドデータメンバーのバインドや、現在のレコードのフィールドに対するさまざまなフラグの設定など、さまざまな操作をサポートしています。 DFX 操作は、`CDaoFieldExchange`の**列挙**型の**FieldType**で定義されている型のレコードセットクラスのデータメンバーに対して実行されます。 使用可能な**FieldType**値は次のとおりです。

- フィールドデータメンバーの `CDaoFieldExchange::outputColumn`。

- パラメーターデータメンバーの `CDaoFieldExchange::param`。

[IsValidOperation](#isvalidoperation)メンバー関数は、独自のカスタム DFX ルーチンを記述するために用意されています。 [SetFieldType](#setfieldtype)は、 [CDaoRecordset::D ofieldexchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)関数で頻繁に使用します。 DFX のグローバル関数の詳細については、「[レコードフィールドエクスチェンジ関数](../../mfc/reference/record-field-exchange-functions.md)」を参照してください。 独自のデータ型のカスタム DFX ルーチンを記述する方法については、「[テクニカルノート 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`CDaoFieldExchange`

## <a name="requirements"></a>要件

**ヘッダー:** afxdao

##  <a name="isvalidoperation"></a>CDaoFieldExchange::IsValidOperation

独自の DFX 関数を記述する場合は、関数の先頭で `IsValidOperation` を呼び出して、現在の操作を特定のフィールドデータメンバー型 (`CDaoFieldExchange::outputColumn` または `CDaoFieldExchange::param`) に対して実行できるかどうかを判断します。

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>戻り値

現在の操作が更新対象のフィールドの型に適している場合は0以外の。

### <a name="remarks"></a>コメント

DFX メカニズムによって実行される操作の一部は、使用可能なフィールドの種類のいずれかにのみ適用されます。 既存の DFX 関数のモデルに従います。

カスタム DFX ルーチンの記述の詳細については、「[テクニカルノート 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)」を参照してください。

##  <a name="m_noperation"></a>CDaoFieldExchange:: m_nOperation

フィールド交換オブジェクトに関連付けられている[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトに対して実行される操作を識別します。

### <a name="remarks"></a>コメント

`CDaoFieldExchange` オブジェクトは、レコードセットに対するさまざまな DFX 操作のコンテキストを提供します。

> [!NOTE]
>  次に示す MarkForAddNew と SetFieldNull 操作の下に記述されている PSEUDONULL 値は、フィールドを Null に設定するために使用される値です。 DAO レコードフィールド交換機構 (DFX) は、この値を使用して、Null として明示的にマークされているフィールドを特定します。 PSEUDONULL フィールドと[COleCurrency](../../mfc/reference/colecurrency-class.md)フィールド[では、](../../atl-mfc-shared/reference/coledatetime-class.md)は必要ありません。

`m_nOperation` に指定できる値は次のとおりです。

|操作|説明|
|---------------|-----------------|
|`AddToParameterList`|SQL ステートメントの**PARAMETERS**句を構築します。|
|`AddToSelectList`|SQL ステートメントの**SELECT**句を構築します。|
|`BindField`|データベース内のフィールドをアプリケーションのメモリ位置にバインドします。|
|`BindParam`|レコードセットのクエリのパラメーター値を設定します。|
|`Fixup`|フィールドの Null 状態を設定します。|
|`AllocCache`|レコードセットの "ダーティ" フィールドを確認するために使用するキャッシュを割り当てます。|
|`StoreField`|現在のレコードをキャッシュに保存します。|
|`LoadField`|キャッシュされたデータメンバー変数をレコードセットに復元します。|
|`FreeCache`|レコードセットの "ダーティ" フィールドを確認するために使用されるキャッシュを解放します。|
|`SetFieldNull`|フィールドの状態を Null に設定し、値を PSEUDONULL に設定します。|
|`MarkForAddNew`|PSEUDONULL でない場合は、"ダーティ" フィールドをマークします。|
|`MarkForEdit`|フィールドがキャッシュと一致しない場合、"ダーティ" フィールドにマークを付けます。|
|`SetDirtyField`|"ダーティ" とマークされたフィールド値を設定します。|
|`DumpField`|フィールドの内容をダンプします (デバッグのみ)。|
|`MaxDFXOperation`|入力チェックに使用されます。|

##  <a name="m_prs"></a>CDaoFieldExchange:: m_prs

`CDaoFieldExchange` オブジェクトに関連付けられた[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトへのポインターを格納します。

### <a name="remarks"></a>コメント

##  <a name="setfieldtype"></a>CDaoFieldExchange::SetFieldType

`CDaoRecordset` クラスの `DoFieldExchange` オーバーライドで `SetFieldType` を呼び出します。

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>パラメーター

*nFieldType*<br/>
`CDaoFieldExchange`で宣言された**列挙型**の値。次のいずれかを指定できます。

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>コメント

通常、ClassWizard はこの呼び出しを書き込みます。 独自の関数を記述し、ウィザードを使用して `DoFieldExchange` 関数を記述する場合は、フィールドマップ外で独自の関数の呼び出しを追加します。 ウィザードを使用しない場合、フィールドマップは表示されません。 この呼び出しは、クラスのフィールドデータメンバーごとに1つずつ、DFX 関数の呼び出しの前に、`CDaoFieldExchange::outputColumn`としてフィールド型を識別します。

レコードセットクラスをパラメーター化する場合は、すべてのパラメーターデータメンバー (フィールドマップの外側) に対して DFX 呼び出しを追加し、これらの呼び出しの前に `SetFieldType`を呼び出す必要があります。 `CDaoFieldExchange::param`値を渡します。 (代わりに、 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)を使用して、そのパラメーター値を設定することができます)。

一般に、フィールドデータメンバーまたはパラメーターデータメンバーに関連付けられている DFX 関数呼び出しの各グループの前に、`SetFieldType`を呼び出す必要があります。 各 `SetFieldType` 呼び出しの*nFieldType*パラメーターは、`SetFieldType` 呼び出しの後にある DFX 関数呼び出しによって表されるデータメンバーの型を識別します。

## <a name="see-also"></a>参照

[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset クラス](../../mfc/reference/cdaorecordset-class.md)
