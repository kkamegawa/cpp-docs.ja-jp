---
title: CDaoFieldInfo 構造体
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: e2638ac908e4e286530301bc913173e87008df47
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303692"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo 構造体

`CDaoFieldInfo` 構造体には、データアクセスオブジェクト (DAO) 用に定義されたフィールドオブジェクトに関する情報が含まれています。

DAO は Office 2013 でサポートされています。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。

## <a name="syntax"></a>構文

```
struct CDaoFieldInfo
{
    CString m_strName;           // Primary
    short m_nType;               // Primary
    long m_lSize;                // Primary
    long m_lAttributes;          // Primary
    short m_nOrdinalPosition;    // Secondary
    BOOL m_bRequired;            // Secondary
    BOOL m_bAllowZeroLength;     // Secondary
    long m_lCollatingOrder;      // Secondary
    CString m_strForeignName;    // Secondary
    CString m_strSourceField;    // Secondary
    CString m_strSourceTable;    // Secondary
    CString m_strValidationRule; // All
    CString m_strValidationText; // All
    CString m_strDefaultValue;   // All
};
```

#### <a name="parameters"></a>パラメーター

*m_strName*<br/>
Field オブジェクトに一意の名前を入力します。 詳細については、DAO ヘルプの「Name プロパティ」を参照してください。

*m_nType*<br/>
フィールドのデータ型を示す値です。 詳細については、DAO ヘルプの「Type プロパティ」を参照してください。 このプロパティの値には、次のいずれかを指定できます。

- `dbBoolean` はい/いいえ、TRUE/FALSE と同じ

- `dbByte` バイト

- `dbInteger` Short

- `dbLong` 長い

- `dbCurrency` 通貨。「MFC クラス[COleCurrency](../../mfc/reference/colecurrency-class.md) 」を参照してください。

- 1つ `dbSingle`

- `dbDouble` Double

- `dbDate` の日付/時刻です。「MFC クラス[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 」を参照してください。

- `dbText` テキスト。「MFC クラス[CString](../../atl-mfc-shared/reference/cstringt-class.md) 」を参照してください。

- `dbLongBinary`Long Binary (OLE オブジェクト); クラス[の代わりに MFC クラス ](../../mfc/reference/cbytearray-class.md)CByteArray`CLongBinary` を使用して、`CByteArray`より豊富で使いやすいものにすることができます。

- `dbMemo` Memo;「MFC クラス `CString`」を参照してください。

- リモートプロシージャコールで使用されるグローバル一意識別子/汎用一意識別子を `dbGUID` します。 詳細については、DAO ヘルプの「Type プロパティ」を参照してください。

> [!NOTE]
>  バイナリデータには文字列データ型を使用しないでください。 これにより、データは Unicode/ANSI 翻訳レイヤーを通過するため、オーバーヘッドが増加し、場合によっては予期しない変換が発生します。

*m_lSize*<br/>
テキストまたは数値を含むフィールドオブジェクトのテキストまたは固定サイズを格納する DAO フィールドオブジェクトの最大サイズをバイト単位で示す値。 詳細については、DAO ヘルプの「Size プロパティ」を参照してください。 サイズには、次のいずれかの値を指定できます。

|種類|サイズ (バイト)|説明|
|----------|--------------------|-----------------|
|`dbBoolean`|1 バイト|はい/いいえ (True/False と同じ)|
|`dbByte`|1|Byte|
|`dbInteger`|2|整数型|
|`dbLong`|4|Long|
|`dbCurrency`|8|通貨 ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|日付/時刻 ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|テキスト ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binary (OLE オブジェクト、[CByteArray](../../mfc/reference/cbytearray-class.md);`CLongBinary`の代わりに使用)|
|`dbMemo`|0|メモ ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|リモートプロシージャコールで使用されるグローバル一意識別子/汎用一意識別子です。|

*m_lAttributes*<br/>
テーブルテーブル、レコードセット、クエリ定義、またはインデックスオブジェクトに含まれる field オブジェクトの特性を指定します。 返される値には、 C++ビットごとの or ( **&#124;** ) 演算子で作成されたこれらの定数の合計を指定できます。

- フィールドサイズが固定されている `dbFixedField` (数値フィールドの既定値)。

- フィールドサイズが可変で `dbVariableField` (テキストフィールドのみ)。

- `dbAutoIncrField` 新しいレコードのフィールド値は、変更できない一意の長整数に自動的にインクリメントされます。 Microsoft Jet データベーステーブルでのみサポートされています。

- `dbUpdatableField` フィールド値を変更できます。

- フィールドが降順 (Z-A または 100-0) の順序で並べ替えられている `dbDescending` (インデックスオブジェクトのフィールドコレクションのフィールドオブジェクトにのみ適用されます。 MFC では、インデックスオブジェクト自体がテーブルグループオブジェクトに含まれています)。 この定数を省略した場合、フィールドは昇順 (A-z または 0-100) の順序 (既定値) で並べ替えられます。

このプロパティの設定を確認するときに、 C++ビットごとの and 演算子 ( **&** ) を使用して、特定の属性をテストできます。 複数の属性を設定する場合は、適切な定数とビットごとの or ( **&#124;** ) 演算子を組み合わせることによって、複数の属性を組み合わせることができます。 詳細については、DAO ヘルプの「Attributes プロパティ」を参照してください。

*m_nOrdinalPosition*<br/>
DAO フィールドオブジェクトによって表されるフィールドを他のフィールドと比較して表示するための数値の順序を指定する値。 このプロパティは、 [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)で設定できます。 詳細については、DAO ヘルプの「OrdinalPosition プロパティ」を参照してください。

*m_bRequired*<br/>
DAO フィールドオブジェクトが Null 以外の値を必要とするかどうかを示します。 このプロパティが TRUE の場合、フィールドには Null 値が許可されません。 [必須] が [FALSE] に設定されている場合、フィールドには、AllowZeroLength プロパティと ValidationRule プロパティの設定で指定された条件を満たす値だけでなく Null 値を含めることができます。 詳細については、DAO ヘルプの「必要なプロパティ」を参照してください。 [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)を使用して、このプロパティを tabledef に設定できます。

*m_bAllowZeroLength*<br/>
空の文字列 ("") が、データ型が Text または Memo の DAO フィールドオブジェクトの有効な値であるかどうかを示します。 このプロパティが TRUE の場合、空の文字列は有効な値です。 このプロパティを FALSE に設定すると、フィールドの値を設定するために空の文字列を使用できないようにすることができます。 詳細については、DAO ヘルプの「AllowZeroLength プロパティ」を参照してください。 [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)を使用して、このプロパティを tabledef に設定できます。

*m_lCollatingOrder*<br/>
文字列比較または並べ替えに使用する、テキスト内の並べ替え順序の順序を指定します。 詳細については、DAO ヘルプのトピック「データアクセスのための Windows レジストリ設定のカスタマイズ」を参照してください。 返される可能性のある値の一覧については、 [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)構造体の `m_lCollatingOrder` メンバーを参照してください。 [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)を使用して、このプロパティを tabledef に設定できます。

*m_strForeignName*<br/>
主テーブルのフィールドに対応する外部テーブル内の DAO フィールドオブジェクトの名前を、リレーションシップで指定する値です。 詳細については、DAO ヘルプの「ForeignName プロパティ」を参照してください。

*m_strSourceField*<br/>
テーブルテーブル、レコードセット、または querydef オブジェクトに含まれる DAO フィールドオブジェクトの元のデータソースであるフィールドの名前を示します。 このプロパティは、フィールドオブジェクトに関連付けられている元のフィールド名を示します。 たとえば、このプロパティを使用して、基になるテーブル内のフィールド名とは無関係の名前を持つクエリフィールド内のデータの元のソースを特定できます。 詳細については、DAO ヘルプの「SourceField, SourceTable Properties」を参照してください。 [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)を使用して、このプロパティを tabledef に設定できます。

*m_strSourceTable*<br/>
テーブルの名前を示します。このテーブルは、テーブルテーブル、レコードセット、または querydef オブジェクトに含まれる DAO フィールドオブジェクトのデータの元のソースです。 このプロパティは、field オブジェクトに関連付けられた元のテーブル名を示します。 たとえば、このプロパティを使用して、基になるテーブル内のフィールド名とは無関係の名前を持つクエリフィールド内のデータの元のソースを特定できます。 詳細については、DAO ヘルプの「SourceField, SourceTable Properties」を参照してください。 [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)を使用して、このプロパティを tabledef に設定できます。

*m_strValidationRule*<br/>
フィールドが変更されたとき、またはテーブルに追加されたときに、そのデータを検証する値。 詳細については、DAO ヘルプの「ValidationRule プロパティ」を参照してください。 [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)を使用して、このプロパティを tabledef に設定できます。

テーブルの定義の関連情報については、 [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)構造体の `m_strValidationRule` メンバーを参照してください。

*m_strValidationText*<br/>
値は、DAO フィールドオブジェクトの値が ValidationRule プロパティの設定で指定された検証規則を満たしていない場合に表示されるメッセージのテキストを指定します。 詳細については、DAO ヘルプのトピック「ValidationText プロパティ」を参照してください。 [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)を使用して、このプロパティを tabledef に設定できます。

*m_strDefaultValue*<br/>
DAO フィールドオブジェクトの既定値。 新しいレコードが作成されると、DefaultValue プロパティの設定がフィールドの値として自動的に入力されます。 詳細については、DAO ヘルプの「DefaultValue プロパティ」を参照してください。 [CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)を使用して、このプロパティを tabledef に設定できます。

## <a name="remarks"></a>コメント

上記の Primary、Secondary、および All への参照は、 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)、 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)、および[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)のクラスの `GetFieldInfo` メンバー関数によって情報がどのように返されるかを示しています。

Field オブジェクトは MFC クラスでは表されません。 代わりに、次のクラスの MFC オブジェクトの基になる DAO オブジェクトには、フィールドオブジェクト ( [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)、 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)、および[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)) のコレクションが含まれています。 これらのクラスは、フィールド情報の一部の項目にアクセスするためのメンバー関数を提供します。また、親オブジェクトの `GetFieldInfo` メンバー関数を呼び出すことによって、`CDaoFieldInfo` オブジェクトを使用して一度にすべてのオブジェクトにアクセスすることもできます。

オブジェクトのプロパティを調べるために使用するだけでなく、`CDaoFieldInfo` を使用して、テーブルテーブルに新しいフィールドを作成するための入力パラメーターを作成することもできます。 このタスクではより単純なオプションを使用できますが、さらに細かい制御が必要な場合は、`CDaoFieldInfo` パラメーターを受け取る[CDaoTableDef:: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)のバージョンを使用できます。

`GetFieldInfo` メンバー関数 (フィールドを含むクラス) によって取得された情報は、`CDaoFieldInfo` 構造体に格納されます。 フィールドオブジェクトが格納されているフィールドコレクションを持つ、内のオブジェクトの `GetFieldInfo` メンバー関数を呼び出します。 `CDaoFieldInfo` は、デバッグビルドで `Dump` メンバー関数も定義します。 `Dump` を使用すると、`CDaoFieldInfo` オブジェクトの内容をダンプできます。

## <a name="requirements"></a>要件

**ヘッダー:** afxdao

## <a name="see-also"></a>参照

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef:: GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset:: GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
