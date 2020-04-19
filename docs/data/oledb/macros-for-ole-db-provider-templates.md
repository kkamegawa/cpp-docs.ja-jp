---
title: OLE DB プロバイダー テンプレート用マクロ
ms.date: 02/11/2019
f1_keywords:
- vc.templates.ole
- BEGIN_PROPERTY_SET
- BEGIN_PROPERTY_SET_EX
- BEGIN_PROPSET_MAP
- CHAIN_PROPERTY_SET
- END_PROPERTY_SET
- END_PROPSET_MAP
- PROPERTY_INFO_ENTRY
- PROPERTY_INFO_ENTRY_EX
- PROPERTY_INFO_ENTRY_VALUE
- BEGIN_PROVIDER_COLUMN_MAP
- END_PROVIDER_COLUMN_MAP
- PROVIDER_COLUMN_ENTRY
- PROVIDER_COLUMN_ENTRY_FIXED
- PROVIDER_COLUMN_ENTRY_GN
- PROVIDER_COLUMN_ENTRY_LENGTH
- PROVIDER_COLUMN_ENTRY_STR
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
- PROVIDER_COLUMN_ENTRY_WSTR
- BEGIN_SCHEMA_MAP
- END_SCHEMA_MAP
- SCHEMA_ENTRY
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
- BEGIN_PROPERTY_SET macro
- BEGIN_PROPERTY_SET_EX macro
- BEGIN_PROPSET_MAP macro
- CHAIN_PROPERTY_SET macro
- END_PROPERTY_SET macro
- END_PROPSET_MAP macro
- PROPERTY_INFO_ENTRY macro
- PROPERTY_INFO_ENTRY_EX macro
- PROPERTY_INFO_ENTRY_VALUE macro
- BEGIN_PROVIDER_COLUMN_MAP macro
- END_PROVIDER_COLUMN_MAP macro
- PROVIDER_COLUMN_ENTRY macro
- PROVIDER_COLUMN_ENTRY_FIXED macro
- PROVIDER_COLUMN_ENTRY_GN macro
- PROVIDER_COLUMN_ENTRY_LENGTH macro
- PROVIDER_COLUMN_ENTRY_STR macro
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
- PROVIDER_COLUMN_ENTRY_WSTR macro
- BEGIN_SCHEMA_MAP macro
- END_SCHEMA_MAP macro
- SCHEMA_ENTRY macro
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
ms.openlocfilehash: f5cf5e8ebadcc48dbd040225496f0a437b92555c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152710"
---
# <a name="macros-for-ole-db-provider-templates"></a>OLE DB プロバイダー テンプレート用マクロ

OLE DB プロバイダー テンプレートのマクロは、次のカテゴリの機能を提供します。

## <a name="property-set-map-macros"></a>プロパティ セットのマップに関するマクロ

|||
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|プロパティ セットの先頭をマークします。|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|プロパティ セットの先頭をマークします。|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|セットのプロパティの先頭をマークを非表示またはプロバイダーのスコープの外部で定義できます。|
|[CHAIN_PROPERTY_SET](#chain_property_set)|プロパティ グループを一緒にチェーンします。|
|[END_PROPERTY_SET](#end_property_set)|プロパティ セットの末尾をマークします。|
|[END_PROPSET_MAP](#end_propset_map)|プロパティ セットのマップの最後をマークします。|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|既定値に設定されたプロパティでは、特定のプロパティを設定します。|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|指定した値に設定されたプロパティでは、特定のプロパティを設定します。 フラグやオプションを設定することもできます。|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|指定した値に設定されたプロパティでは、特定のプロパティを設定します。|

## <a name="column-map-macros"></a>列マップに関するマクロ

|||
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|プロバイダーの列のマップ エントリの先頭をマークします。|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|プロバイダーの列のマップ エントリの終了を示します。|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|プロバイダーでサポートされている特定の列を表します。|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|プロバイダーでサポートされている特定の列を表します。 列のデータ型を指定することができます。|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|プロバイダーでサポートされている特定の列を表します。 列のサイズ、データ型、有効桁数、スケール、およびスキーマ行セット GUID を指定することができます。|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|プロバイダーでサポートされている特定の列を表します。 列のサイズを指定することができます。|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|プロバイダーでサポートされている特定の列を表します。 列の型が文字列と見なします。|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|プロバイダーでサポートされている特定の列を表します。 PROVIDER_COLUMN_ENTRY_LENGTH が列のデータ型やサイズを指定することもできます。|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|プロバイダーでサポートされている特定の列を表します。 これにより、列の型が Unicode 文字の文字列を前提としています。|

## <a name="schema-rowset-macros"></a>スキーマ行セットのマクロ

|||
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|スキーマ マップの先頭をマークします。|
|[END_SCHEMA_MAP](#end_schema_map)|スキーマ マップの最後をマークします。|
|[SCHEMA_ENTRY](#schema_entry)|GUID をクラスに関連付けます。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

### <a name="begin_property_set"></a> BEGIN_PROPERTY_SET

プロパティのセットのプロパティの先頭をマークは、マップを設定します。

#### <a name="syntax"></a>構文

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>パラメーター

*guid*<br/>
[in]プロパティの GUID。

#### <a name="example"></a>例

「 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)」を参照してください。

### <a name="begin_property_set_ex"></a> BEGIN_PROPERTY_SET_EX

プロパティのセットのプロパティの先頭をマークは、マップを設定します。

#### <a name="syntax"></a>構文

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>パラメーター

*guid*<br/>
[in]プロパティの GUID。

*flags*<br/>
[in]すべてのプロパティ セットを公開したくないまたはプロバイダーのスコープ外で定義されたプロパティを公開するプロバイダーの UPROPSET_PASSTHROUGH UPROPSET_HIDDEN します。

#### <a name="example"></a>例

「 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)」を参照してください。

### <a name="begin_propset_map"></a> BEGIN_PROPSET_MAP

プロパティのセットのマップ エントリを示します。

#### <a name="syntax"></a>構文

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>パラメーター

*Class*<br/>
[in]このプロパティが設定されているクラスを指定します。 プロパティ セットは、次の OLE DB オブジェクトで指定できます。

- [データ ソース オブジェクト](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [セッション オブジェクト](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [[コマンド]](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>例

プロパティ セット マップのコード例を次に示します。

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a> CHAIN_PROPERTY_SET

このマクロは、プロパティ グループを連結します。

#### <a name="syntax"></a>構文

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>パラメーター

*ChainClass*<br/>
[in]プロパティにチェーンするクラスの名前。 これは、(セッション、コマンド、またはデータ ソース オブジェクト クラス) などのマップが既に含まれている ATL プロジェクト ウィザードによって生成されるクラスです。

#### <a name="remarks"></a>Remarks

独自のクラスを別のクラスからプロパティ セットを連結し、クラスから直接、プロパティにアクセスできます。

> [!CAUTION]
>  このマクロを多用します。 不適切な使用には、コンシューマーが OLE DB 準拠合致テストが失敗する可能性があります。

### <a name="end_property_set"></a> END_PROPERTY_SET

プロパティ セットの末尾をマークします。

#### <a name="syntax"></a>構文

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>パラメーター

*guid*<br/>
[in]プロパティの GUID。

#### <a name="example"></a>例

「 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)」を参照してください。

### <a name="end_propset_map"></a> END_PROPSET_MAP

プロパティの終了セットのマップ エントリを示します。

#### <a name="syntax"></a>構文

```cpp
END_PROPSET_MAP()
```

#### <a name="example"></a>例

「 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)」を参照してください。

### <a name="property_info_entry"></a> PROPERTY_INFO_ENTRY

プロパティ セットの特定のプロパティを表します。

#### <a name="syntax"></a>構文

```cpp
PROPERTY_INFO_ENTRY(dwPropID)
```

#### <a name="parameters"></a>パラメーター

*dwPropID*<br/>
[入力] プロパティ セット GUID と組み合わせて使用してプロパティを特定する [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 値。

#### <a name="remarks"></a>Remarks

このマクロは、 `DWORD` 型のプロパティ値を、ATLDB.H で定義された既定値に設定します。 選択した値にプロパティを設定するには、 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)を使用します。 設定する、`VARTYPE`と[DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85))と同時に、プロパティを使用して[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)します。

#### <a name="example"></a>例

「 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)」を参照してください。

### <a name="property_info_entry_ex"></a> PROPERTY_INFO_ENTRY_EX

プロパティ セットの特定のプロパティを表します。

#### <a name="syntax"></a>構文

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>パラメーター

*dwPropID*<br/>
[入力] プロパティ セット GUID と組み合わせて使用してプロパティを特定する [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 値。

*vt*<br/>
[入力] このプロパティ エントリの `VARTYPE`。 (Wtypes.h で定義)

*dwFlags*<br/>
[入力] このプロパティ エントリを記述している [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) 値。

*値*<br/>
[入力] `DWORD`型のプロパティ値。

*options*<br/>
DBPROPOPTIONS_REQUIRED または DBPROPOPTIONS_SETIFCHEAP のいずれか。 通常、プロバイダーは、設定する必要はありません*オプション*コンシューマーによって設定されているためです。

#### <a name="remarks"></a>Remarks

このマクロでは、オプションとフラグだけでなく、 `DWORD` 型のプロパティの値を直接指定できます。 単にプロパティを ATLDB.H に定義されている既定値に設定するには、 [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)を使用します。 オプションやフラグを設定せずに任意の値にプロパティを設定するには、 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)を使用します。

#### <a name="example"></a>例

「 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)」を参照してください。

### <a name="property_info_entry_value"></a> PROPERTY_INFO_ENTRY_VALUE

プロパティ セットの特定のプロパティを表します。

#### <a name="syntax"></a>構文

```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)
```

#### <a name="parameters"></a>パラメーター

*dwPropID*<br/>
[入力] プロパティ セット GUID と組み合わせて使用してプロパティを特定する [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 値。

*value*<br/>
[入力] `DWORD`型のプロパティ値。

#### <a name="remarks"></a>Remarks

このマクロでは、型のプロパティ値を直接指定できる`DWORD`します。 既定値にプロパティを設定します。H、使用[PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)します。 値、フラグ、およびプロパティのオプションを設定するには、使用[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)します。

#### <a name="example"></a>例

「 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)」を参照してください。

### <a name="begin_provider_column_map"></a> BEGIN_PROVIDER_COLUMN_MAP

プロバイダーの列のマップ エントリの先頭をマークします。

#### <a name="syntax"></a>構文

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>パラメーター

*クラス*<br/>
[in]このマップが属するクラスの名前。

#### <a name="example"></a>例

プロバイダー列マップのコード例を次に示します。

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a> END_PROVIDER_COLUMN_MAP

プロバイダーの列のマップ エントリの終了を示します。

#### <a name="syntax"></a>構文

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>例

参照してください[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)します。

### <a name="provider_column_entry"></a> PROVIDER_COLUMN_ENTRY

プロバイダーでサポートされている特定の列を表します。

#### <a name="syntax"></a>構文

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
[in]列の名前。

*序数*<br/>
[in]列の番号。 列は、ブックマーク列でない限り、列の番号は 0 をできません。

*member*<br/>
[in]メンバー変数`dataClass`列に対応します。

### <a name="provider_column_entry_fixed"></a> PROVIDER_COLUMN_ENTRY_FIXED

プロバイダーでサポートされている特定の列を表します。

#### <a name="syntax"></a>構文

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
[in]列の名前。

*序数*<br/>
[in]列の番号。 列は、ブックマーク列でない限り、列の番号は 0 をできません。

*dbtype*<br/>
[in]データ型[DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85))します。

*member*<br/>
[in]メンバー変数`dataClass`データを格納します。

#### <a name="remarks"></a>Remarks

列のデータ型を指定することができます。

#### <a name="example"></a>例

参照してください[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)します。

### <a name="provider_column_entry_gn"></a> PROVIDER_COLUMN_ENTRY_GN

プロバイダーでサポートされている特定の列を表します。

#### <a name="syntax"></a>構文

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
[in]列の名前。

*序数*<br/>
[in]列の番号。 列は、ブックマーク列でない限り、列の番号は 0 をできません。

*flags*<br/>
[in]データを返す方法を指定します。 参照してください、`dwFlags`説明[DBBINDING 構造体](/previous-versions/windows/desktop/ms716845(v=vs.85))します。

*colSize*<br/>
[in]列のサイズ。

*dbtype*<br/>
[in]値のデータ型を示します。 参照してください、`wType`説明[DBBINDING 構造体](/previous-versions/windows/desktop/ms716845(v=vs.85))します。

*precision*<br/>
[in]場合は、データを取得するときに使用する桁数を示します*dbType* DBTYPE_NUMERIC または DBTYPE_DECIMAL です。 参照してください、`bPrecision`説明[DBBINDING 構造体](/previous-versions/windows/desktop/ms716845(v=vs.85))します。

*scale*<br/>
[in]DbType が DBTYPE_NUMERIC または DBTYPE_DECIMAL の場合は、データを取得するときに使用する小数点以下桁数を示します。 参照してください、`bScale`説明[DBBINDING 構造体](/previous-versions/windows/desktop/ms716845(v=vs.85))します。

*guid*<br/>
スキーマ行セットの GUID。 参照してください[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*スキーマ行セットとその Guid の一覧についてはします。

#### <a name="remarks"></a>Remarks

列のサイズ、データ型、有効桁数、スケール、およびスキーマ行セット GUID を指定することができます。

### <a name="provider_column_entry_length"></a> PROVIDER_COLUMN_ENTRY_LENGTH

プロバイダーでサポートされている特定の列を表します。

#### <a name="syntax"></a>構文

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
[in]列の名前。

*序数*<br/>
[in]列の番号。 列は、ブックマーク列でない限り、列の番号は 0 をできません。

*size*<br/>
[in]列のサイズ (バイト単位)。

*member*<br/>
[in]メンバー変数`dataClass`列のデータを格納します。

#### <a name="remarks"></a>Remarks

列のサイズを指定することができます。

#### <a name="example"></a>例

参照してください[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)します。

### <a name="provider_column_entry_str"></a> PROVIDER_COLUMN_ENTRY_STR

プロバイダーでサポートされている特定の列を表します。

#### <a name="syntax"></a>構文

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
[in]列の名前。

*序数*<br/>
[in]列の番号。 列は、ブックマーク列でない限り、列の番号は 0 をできません。

*member*<br/>
[in]データを格納するデータ クラスのメンバー変数です。

#### <a name="remarks"></a>Remarks

このマクロを使用して列のデータがあると見なされますと[DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85))します。

#### <a name="example"></a>例

参照してください[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)します。

### <a name="provider_column_entry_type_length"></a> PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

プロバイダーでサポートされている特定の列を表します。

#### <a name="syntax"></a>構文

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
[in]列の名前。

*序数*<br/>
[in]列の番号。 列は、ブックマーク列でない限り、列の番号は 0 をできません。

*dbtype*<br/>
[in]データ型[DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85))します。

*size*<br/>
[in]列のサイズ (バイト単位)。

*member*<br/>
[in]データを格納するデータ クラスのメンバー変数です。

#### <a name="remarks"></a>Remarks

ような[PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md)が列のデータ型やサイズを指定することもできます。

### <a name="provider_column_entry_wstr"></a> PROVIDER_COLUMN_ENTRY_WSTR

プロバイダーでサポートされている特定の列を表します。

#### <a name="syntax"></a>構文

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
[in]列の名前。

*序数*<br/>
[in]列の番号。 列は、ブックマーク列でない限り、列の番号は 0 をできません。

*member*<br/>
[in]データを格納するデータ クラスのメンバー変数です。

#### <a name="remarks"></a>Remarks

列のデータが null 値が Unicode 文字の文字列を終了するときに、このマクロを使用[DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85))します。

### <a name="begin_schema_map"></a> BEGIN_SCHEMA_MAP

スキーマ マップの先頭を示します。

#### <a name="syntax"></a>構文

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>パラメーター

*SchemaClass*<br/>
マップを含むクラスです。 通常、セッション クラスになります。

#### <a name="remarks"></a>Remarks

参照してください[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))スキーマ行セットの詳細については、Windows SDK に含まれています。

### <a name="end_schema_map"></a> END_SCHEMA_MAP

スキーマ マップの終了を示します。

#### <a name="syntax"></a>構文

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>Remarks

詳細については、次を参照してください。 [IDBSchemaRowsetImpl クラス](../../data/oledb/idbschemarowsetimpl-class.md)します。

### <a name="schema_entry"></a> SCHEMA_ENTRY

GUID をクラスに関連付けます。

#### <a name="syntax"></a>構文

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>パラメーター

*guid*<br/>
スキーマ行セットの GUID。 参照してください[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*スキーマ行セットとその Guid の一覧についてはします。

*rowsetClass*<br/>
このクラスは、スキーマ行セットを表すために作成されます。

#### <a name="remarks"></a>Remarks

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)クエリ、Guid の一覧については、マップ、ことができます。 または、GUID が指定された場合、行セットを作成できます。 スキーマ行セット`IDBSchemaRowsetImpl`作成は標準に似ています`CRowsetImpl`-派生クラスを提供する点を除いて、`Execute`を次のシグネチャを持つメソッド。

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

これは、`Execute`関数は、行セットのデータを設定します。 ATL プロジェクト ウィザードを作成する」の説明に従って[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*、3 つの必須の OLE DB スキーマの各プロジェクトのスキーマ行セットの初期 3。

- DBSCHEMA_TABLES

- DBSCHEMA_COLUMNS

- DBSCHEMA_PROVIDER_TYPES

ウィザードでは、スキーマ マップに対応する 3 つのエントリも追加されます。 参照してください[OLE DB テンプレート プロバイダーの作成](../../data/oledb/creating-an-ole-db-provider.md)詳細については、ウィザードを使用してプロバイダーを作成します。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[OLE DB プロバイダーの作成](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB プロバイダー テンプレート リファレンス](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB プロバイダー テンプレート用マクロ](../../data/oledb/macros-for-ole-db-provider-templates.md)