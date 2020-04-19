---
title: CDBPropSet クラス
ms.date: 11/04/2016
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
- CDBPropSet.CDBPropSet
- CDBPropSet::CDBPropSet
- ATL::CDBPropSet::CDBPropSet
- ATL.CDBPropSet.CDBPropSet
- CDBPropSet.operator=
- ATL::CDBPropSet::operator=
- ATL.CDBPropSet.operator=
- CDBPropSet::operator=
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- SetGUID
- CDBPropSet::SetGUID
helpviewer_keywords:
- CDBPropSet class
- AddProperty method
- CDBPropSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
- AddProperty method
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
ms.openlocfilehash: b58c0262d361ede37bc3db68784177ec4c29f3a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325027"
---
# <a name="cdbpropset-class"></a>CDBPropSet クラス

継承、`DBPROPSET`構造体し、キー フィールドを初期化するコンス トラクターを追加するだけでなく`AddProperty`メソッドにアクセスします。

## <a name="syntax"></a>構文

```cpp
class CDBPropSet : public tagDBPROPSET
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[AddProperty](#addproperty)|プロパティ セットには、プロパティを追加します。|
|[CDBPropSet](#cdbpropset)|コンストラクターです。|
|[SetGUID](#setguid)|セット、`guidPropertySet`のフィールド、`DBPROPSET`構造体。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator=](#op_equal)|1 つのプロパティ セットを他の内容を割り当てます。|

## <a name="remarks"></a>Remarks

OLE DB プロバイダーとコンシューマー使用`DBPROPSET`構造体の配列を渡す`DBPROP`構造体。 各`DBPROP`構造体は、設定可能な 1 つのプロパティを表します。

## <a name="addproperty"></a> Cdbpropset::addproperty

プロパティ セットには、プロパティを追加します。

### <a name="syntax"></a>構文

```cpp
bool AddProperty(DWORD dwPropertyID,
   constVARIANT& var,
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCSTR szValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCWSTR szValue,DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   bool bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   BYTE bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   short nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   long nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   float fltValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   double dblValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   CY cyValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();
```

#### <a name="parameters"></a>パラメーター

*dwPropertyID*<br/>
[in]追加するプロパティの ID。 初期化に使用される、`dwPropertyID`の`DBPROP`構造、プロパティ セットに追加します。

*var*<br/>
[in]プロパティ値を初期化するために使用されるバリアント、`DBPROP`構造、プロパティ セットに追加します。

*szValue*<br/>
[in]プロパティ値を初期化するために使用する文字列、`DBPROP`構造、プロパティ セットに追加します。

*bValue*<br/>
[in]A`BYTE`またはのプロパティ値を初期化するために使用するブール値、`DBPROP`構造、プロパティ セットに追加します。

*nValue*<br/>
[in]プロパティ値を初期化するために使用する整数値、`DBPROP`構造、プロパティ セットに追加します。

*fltValue*<br/>
[in]プロパティ値を初期化するために使用する浮動小数点値、`DBPROP`構造、プロパティ セットに追加します。

*dblValue*<br/>
[in]倍精度浮動小数点値のプロパティ値を初期化するために使用される、`DBPROP`構造、プロパティ セットに追加します。

*cyValue*<br/>
[in]CY 通貨値のプロパティ値を初期化するために使用される、`DBPROP`構造、プロパティ セットに追加します。

### <a name="return-value"></a>戻り値

**true**場合は、プロパティが正常に追加します。 それ以外の場合、 **false**します。

## <a name="cdbpropset"></a> Cdbpropset::cdbpropset

コンストラクターです。 初期化します、 `rgProperties`、 `cProperties`、および`guidPropertySet`のフィールド、 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))構造体。

### <a name="syntax"></a>構文

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>パラメーター

*guid*<br/>
[in]初期化するために使用される GUID、`guidPropertySet`フィールド。

*propset*<br/>
[in]もう 1 つ`CDBPropSet`オブジェクトのコピー構築します。

## <a name="setguid"></a> Cdbpropset::setguid

セット、`guidPropertySet`フィールドに、`DBPROPSET`構造体。

### <a name="syntax"></a>構文

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>パラメーター

*guid*<br/>
[in]GUID を設定するため、`guidPropertySet`のフィールド、 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))構造体。

### <a name="remarks"></a>Remarks

このフィールドを設定することができます、[コンス トラクター](../../data/oledb/cdbpropset-cdbpropset.md)もします。

## <a name="op_equal"></a> Cdbpropset::operator =

もう 1 つのプロパティ セットに設定する 1 つのプロパティの内容を割り当てます。

### <a name="syntax"></a>構文

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet クラス](../../data/oledb/cdbpropidset-class.md)<br/>
[DBPROPSET 構造体](/previous-versions/windows/desktop/ms714367(v=vs.85))
[DBPROP 構造体](/previous-versions/windows/desktop/ms717970(v=vs.85))