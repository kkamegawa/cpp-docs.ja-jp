---
title: CDBPropIDSet クラス
ms.date: 11/04/2016
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
- CDBPropIDSet.AddPropertyID
- CDBPropIDSet::AddPropertyID
- AddPropertyID
- ATL.CDBPropIDSet.AddPropertyID
- ATL::CDBPropIDSet::AddPropertyID
- ATL::CDBPropIDSet::CDBPropIDSet
- CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet.operator=
- ATL.CDBPropIDSet.operator=
- ATL::CDBPropIDSet::operator=
- CDBPropIDSet::operator=
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- SetGUID
- ATL.CDBPropIDSet.SetGUID
- CDBPropIDSet::SetGUID
helpviewer_keywords:
- CDBPropIDSet class
- AddPropertyID method
- CDBPropIDSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
ms.openlocfilehash: 9e878af3acf4c4d3a6ca785454c4bb072f17cf09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209322"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet クラス

継承、`DBPROPIDSET`構造体し、キー フィールドを初期化するコンス トラクターを追加するだけでなく[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)メソッドにアクセスします。

## <a name="syntax"></a>構文

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[AddPropertyID](#addpropertyid)|プロパティ ID の設定にプロパティを追加します。|
|[CDBPropIDSet](#cdbpropidset)|コンストラクターです。|
|[SetGUID](#setguid)|プロパティ ID の GUID のセットを設定します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator=](#op_equal)|割り当て ID の 1 つのプロパティの内容は別に設定します。|

## <a name="remarks"></a>Remarks

OLE DB コンシューマー使用`DBPROPIDSET`をコンシューマーがプロパティの情報を取得するプロパティ Id の配列を渡すための構造体。 1 つで指定されたプロパティ[コンス トラクターは](/previous-versions/windows/desktop/ms717981(v=vs.85))構造体が 1 つのプロパティ セットに属しています。

## <a name="addpropertyid"></a> CDBPropIDSet::AddPropertyID

プロパティ ID の設定には、プロパティ ID を追加します。

### <a name="syntax"></a>構文

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>パラメーター

*propid*<br/>
[in]プロパティ ID に追加するプロパティ ID を設定します。

## <a name="cdbpropidset"></a> Cdbpropidset::cdbpropidset

コンストラクターです。 初期化します、 `rgProperties`、 `cProperties`、および (必要に応じて)`guidPropertySet`のフィールド、[コンス トラクターは](/previous-versions/windows/desktop/ms717981(v=vs.85))構造体。

### <a name="syntax"></a>構文

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>パラメーター

*guid*<br/>
[in]初期化するために使用される GUID、`guidPropertySet`フィールド。

*propidset*<br/>
[in]もう 1 つ`CDBPropIDSet`オブジェクトのコピー構築します。

## <a name="setguid"></a> Cdbpropidset::setguid

[GUID] フィールドを設定、`DBPROPIDSET`構造体。

### <a name="syntax"></a>構文

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>パラメーター

*guid*<br/>
[in]GUID を設定するため、`guidPropertySet`のフィールド、[コンス トラクターは](/previous-versions/windows/desktop/ms717981(v=vs.85))構造体。

### <a name="remarks"></a>Remarks

このフィールドを設定することができます、[コンス トラクター](../../data/oledb/cdbpropidset-cdbpropidset.md)もします。 このクラスの既定のコンス トラクターを使用する場合は、この関数を呼び出します。

## <a name="op_equal"></a> Cdbpropidset::operator =

1 つのプロパティ ID のセットを別の ID プロパティ セットの内容を割り当てます。

### <a name="syntax"></a>構文

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)