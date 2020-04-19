---
title: CSimpleMap クラス
ms.date: 11/04/2016
f1_keywords:
- CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayElementType
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayKeyType
- ATLSIMPCOLL/ATL::CSimpleMap::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::Add
- ATLSIMPCOLL/ATL::CSimpleMap::FindKey
- ATLSIMPCOLL/ATL::CSimpleMap::FindVal
- ATLSIMPCOLL/ATL::CSimpleMap::GetKeyAt
- ATLSIMPCOLL/ATL::CSimpleMap::GetSize
- ATLSIMPCOLL/ATL::CSimpleMap::GetValueAt
- ATLSIMPCOLL/ATL::CSimpleMap::Lookup
- ATLSIMPCOLL/ATL::CSimpleMap::Remove
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleMap::ReverseLookup
- ATLSIMPCOLL/ATL::CSimpleMap::SetAt
- ATLSIMPCOLL/ATL::CSimpleMap::SetAtIndex
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
ms.openlocfilehash: afd9f017bb0fb9a95a0ed4fd135dcbd5ea4ddba2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277943"
---
# <a name="csimplemap-class"></a>CSimpleMap クラス

このクラスは、単純なマッピングの配列のサポートを提供します。

## <a name="syntax"></a>構文

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>パラメーター

*TKey*<br/>
キーの要素の型。

*TVal*<br/>
要素の値の型。

*TEqual*<br/>
型の要素に対して等値テストを定義する、特徴オブジェクト`T`します。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|値の型の Typedef。|
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|キーの種類の Typedef。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSimpleMap::CSimpleMap](#csimplemap)|コンストラクターです。|
|[CSimpleMap::~CSimpleMap](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSimpleMap::Add](#add)|マップの配列には、キーと関連付けられている値を追加します。|
|[CSimpleMap::FindKey](#findkey)|特定のキーを検索します。|
|[CSimpleMap::FindVal](#findval)|特定の値を検索します。|
|[CSimpleMap::GetKeyAt](#getkeyat)|指定したキーを取得します。|
|[CSimpleMap::GetSize](#getsize)|マッピングの配列内のエントリの数を返します。|
|[CSimpleMap::GetValueAt](#getvalueat)|指定した値を取得します。|
|[CSimpleMap::Lookup](#lookup)|指定したキーに関連付けられている値を返します。|
|[CSimpleMap::Remove](#remove)|キーと一致する値を削除します。|
|[CSimpleMap::RemoveAll](#removeall)|すべてのキーと値を削除します。|
|[CSimpleMap::RemoveAt](#removeat)|特定のキーと一致する値を削除します。|
|[CSimpleMap::ReverseLookup](#reverselookup)|指定された値に関連付けられているキーを返します。|
|[CSimpleMap::SetAt](#setat)|指定したキーに関連付けられている値を設定します。|
|[CSimpleMap::SetAtIndex](#setatindex)|特定のキーと値を設定します。|

## <a name="remarks"></a>Remarks

`CSimpleMap` 指定された型の単純なマッピングの配列をサポート`T`、順序付けられていない主な要素と関連付けられた値の配列を管理します。

パラメーター`TEqual`型の 2 つの要素に対して等値関数を定義する手段を提供します`T`します。 ようなクラスを作成して[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)、すべての指定された配列の等値テストの動作を変更することはできます。 たとえば、ポインターの配列を扱う場合、ポインターが参照値に応じてとして等価性を定義すると便利ですがあります。 既定の実装を利用**operator==()** します。

両方`CSimpleMap`と[CSimpleArray](../../atl/reference/csimplearray-class.md)以前の ATL との互換性をリリースするより完全かつ効率的なコレクションの実装が提供される[CAtlArray](../../atl/reference/catlarray-class.md)と[CAtlMap](../../atl/reference/catlmap-class.md)します。

ATL と MFC での他のマップ コレクションとは異なりこのクラスは単純な配列と検索順次検索が必要です。 `CAtlMap` 配列には、多数の要素が含まれている場合に使用する必要があります。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsimpcoll.h

## <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

##  <a name="add"></a>  CSimpleMap::Add

マップの配列には、キーと関連付けられている値を追加します。

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
キー。

*val*<br/>
関連する値。

### <a name="return-value"></a>戻り値

かどうか、キーと値が正常に追加されたそれ以外の場合は TRUE を返します。

### <a name="remarks"></a>Remarks

各キーと値のペアは、マップ配列のメモリが解放され、再割り当て、各データは常に連続して格納することを確認するにはエラーの原因を追加します。 2 番目のキー要素常に直接依存してメモリ内の最初のキー要素など。

##  <a name="_arrayelementtype"></a>  CSimpleMap::_ArrayElementType

キーの種類の typedef。

```
typedef TVal _ArrayElementType;
```

##  <a name="_arraykeytype"></a>  CSimpleMap::_ArrayKeyType

値の型の typedef。

```
typedef TKey _ArrayKeyType;
```

##  <a name="csimplemap"></a>  CSimpleMap::CSimpleMap

コンストラクターです。

```
CSimpleMap();
```

### <a name="remarks"></a>Remarks

データ メンバーを初期化します。

##  <a name="dtor"></a>  CSimpleMap::~CSimpleMap

デストラクターです。

```
~CSimpleMap();
```

### <a name="remarks"></a>Remarks

割り当てられているすべてのリソースを解放します。

##  <a name="findkey"></a>  CSimpleMap::FindKey

特定のキーを検索します。

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>パラメーター

*key*<br/>
検索対象のキー。

### <a name="return-value"></a>戻り値

存在する場合は、キーのインデックスを返しますそれ以外の場合は-1 を返します。

##  <a name="findval"></a>  CSimpleMap::FindVal

特定の値を検索します。

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>パラメーター

*val*<br/>
検索対象の値。

### <a name="return-value"></a>戻り値

値のインデックスが見つかった場合は、それ以外の場合は-1 を返しますを返します。

##  <a name="getkeyat"></a>  CSimpleMap::GetKeyAt

指定したインデックス位置にあるキーを取得します。

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
返すキーのインデックス。

### <a name="return-value"></a>戻り値

によって参照されるキーを返します*nIndex*します。

### <a name="remarks"></a>Remarks

渡されたインデックス*nIndex*に意味のある戻り値に対して有効である必要があります。

##  <a name="getsize"></a>  CSimpleMap::GetSize

マッピングの配列内のエントリの数を返します。

```
int GetSize() const;
```

### <a name="return-value"></a>戻り値

マッピングの配列 (キーと値は 1 つのエントリ) のエントリの数を返します。

##  <a name="getvalueat"></a>  CSimpleMap::GetValueAt

特定のインデックス位置にある値を取得します。

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
戻り値のインデックス。

### <a name="return-value"></a>戻り値

によって参照される値を返します*nIndex*します。

### <a name="remarks"></a>Remarks

渡されたインデックス*nIndex*に意味のある戻り値に対して有効である必要があります。

##  <a name="lookup"></a>  CSimpleMap::Lookup

指定したキーに関連付けられている値を返します。

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>パラメーター

*key*<br/>
キー。

### <a name="return-value"></a>戻り値

関連付けられている値を返します。 一致するキーが存在すると、NULL がない場合が返されます。

##  <a name="remove"></a>  CSimpleMap::Remove

キーと一致する値を削除します。

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
キー。

### <a name="return-value"></a>戻り値

かどうか、キーと一致する値は、正常に削除された場合は FALSE それ以外の場合は TRUE を返します。

##  <a name="removeall"></a>  CSimpleMap::RemoveAll

すべてのキーと値を削除します。

```
void RemoveAll();
```

### <a name="remarks"></a>Remarks

マッピングの配列オブジェクトからすべてのキーと値を削除します。

##  <a name="removeat"></a>  CSimpleMap::RemoveAt

キーと指定したインデックスに関連付けられている値を削除します。

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
キーと関連付けられている値を削除するインデックス。

### <a name="return-value"></a>戻り値

指定されたインデックスが無効なインデックスの場合は、成功した場合、FALSE の TRUE を返します。

##  <a name="reverselookup"></a>  CSimpleMap::ReverseLookup

指定された値に関連付けられているキーを返します。

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>パラメーター

*val*<br/>
値。

### <a name="return-value"></a>戻り値

関連付けられたキーを返します。 一致するキーが存在すると、NULL がない場合が返されます。

##  <a name="setat"></a>  CSimpleMap::SetAt

指定したキーに関連付けられている値を設定します。

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
キー。

*val*<br/>
割り当てる新しい値。

### <a name="return-value"></a>戻り値

キーが検出されましたが、いて、値が正常に変更はそれ以外の場合は TRUE を返します。

##  <a name="setatindex"></a>  CSimpleMap::SetAtIndex

指定したインデックス位置にあるキーと値を設定します。

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
キーと値のペアを変更するを参照するインデックス。

*key*<br/>
新しいキー。

*val*<br/>
新しい値。

### <a name="return-value"></a>戻り値

TRUE を返します正常に終了したかどうか、インデックスが無効です。

### <a name="remarks"></a>Remarks

キーと値によって示される更新*nIndex*します。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
