---
title: CSimpleArray クラス
ms.date: 11/04/2016
f1_keywords:
- CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::Add
- ATLSIMPCOLL/ATL::CSimpleArray::Find
- ATLSIMPCOLL/ATL::CSimpleArray::GetData
- ATLSIMPCOLL/ATL::CSimpleArray::GetSize
- ATLSIMPCOLL/ATL::CSimpleArray::Remove
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleArray::SetAtIndex
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
ms.openlocfilehash: 8c050002549fc6b7a18acb34f0e4f9a2f278db82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278008"
---
# <a name="csimplearray-class"></a>CSimpleArray クラス

このクラスは、単純な配列を管理するためのメソッドを提供します。

## <a name="syntax"></a>構文

```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>
class CSimpleArray
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
配列に格納するデータの型。

*TEqual*<br/>
型の要素に対して等値テストを定義する、特徴オブジェクト*T*します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSimpleArray::CSimpleArray](#csimplearray)|単純な配列のコンス トラクター。|
|[CSimpleArray:: ~ CSimpleArray](#dtor)|単純な配列のデストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSimpleArray::Add](#add)|配列に新しい要素を追加します。|
|[CSimpleArray::Find](#find)|配列の要素を検索します。|
|[CSimpleArray::GetData](#getdata)|配列に格納されているデータへのポインターを返します。|
|[CSimpleArray::GetSize](#getsize)|配列に格納されている要素の数を返します。|
|[CSimpleArray::Remove](#remove)|配列から指定された要素を削除します。|
|[CSimpleArray::RemoveAll](#removeall)|配列からすべての要素を削除します。|
|[CSimpleArray::RemoveAt](#removeat)|配列から指定した要素を削除します。|
|[CSimpleArray::SetAtIndex](#setatindex)|配列内の指定した要素を設定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CSimpleArray::operator\[\]](#operator_at)|配列から要素を取得します。|
|[CSimpleArray::operator =](#operator_eq)|代入演算子。|

## <a name="remarks"></a>Remarks

`CSimpleArray` 作成して、指定された型の単純な配列を管理するメソッドを提供`T`します。

パラメーター`TEqual`型の 2 つの要素に対して等値関数を定義する手段を提供します`T`します。 ようなクラスを作成して[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)、すべての指定された配列の等値テストの動作を変更することはできます。 たとえば、ポインターの配列を扱う場合、ポインターが参照値に応じてとして等価性を定義すると便利ですがあります。 既定の実装を利用**operator=()** します。

両方`CSimpleArray`と[CSimpleMap](../../atl/reference/csimplemap-class.md)要素の数が少ない場合に設計されています。 [CAtlArray](../../atl/reference/catlarray-class.md)と[CAtlMap](../../atl/reference/catlmap-class.md)配列には、多数の要素が含まれている場合に使用する必要があります。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsimpcoll.h

## <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]

##  <a name="add"></a>  CSimpleArray::Add

配列に新しい要素を追加します。

```
BOOL Add(const T& t);
```

### <a name="parameters"></a>パラメーター

*t*<br/>
配列に追加する要素。

### <a name="return-value"></a>戻り値

かどうか、要素が正常に追加した配列では、FALSE にそれ以外の場合は TRUE を返します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]

##  <a name="csimplearray"></a>  CSimpleArray::CSimpleArray

配列オブジェクトのコンス トラクターです。

```
CSimpleArray(const CSimpleArray<T, TEqual>& src);
CSimpleArray();
```

### <a name="parameters"></a>パラメーター

*src*<br/>
既存の `CSimpleArray` オブジェクト。

### <a name="remarks"></a>Remarks

新しい空の作成、データ メンバーは初期化`CSimpleArray`オブジェクト、または、既存のコピーを`CSimpleArray`オブジェクト。

##  <a name="dtor"></a>  CSimpleArray:: ~ CSimpleArray

デストラクターです。

```
~CSimpleArray();
```

### <a name="remarks"></a>Remarks

割り当てられているすべてのリソースを解放します。

##  <a name="find"></a>  CSimpleArray::Find

配列の要素を検索します。

```
int Find(const T& t) const;
```

### <a name="parameters"></a>パラメーター

*t*<br/>
検索対象の要素。

### <a name="return-value"></a>戻り値

要素が見つからない場合は、見つかった要素のインデックスを返します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]

##  <a name="getdata"></a>  CSimpleArray::GetData

配列に格納されているデータへのポインターを返します。

```
T* GetData() const;
```

### <a name="return-value"></a>戻り値

配列内のデータへのポインターを返します。

##  <a name="getsize"></a>  CSimpleArray::GetSize

配列に格納されている要素の数を返します。

```
int GetSize() const;
```

### <a name="return-value"></a>戻り値

配列に格納されている要素の数を返します。

##  <a name="operator_at"></a>  CSimpleArray::operator \[\]

配列から要素を取得します。

```
T& operator[](int nindex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
要素のインデックス。

### <a name="return-value"></a>戻り値

によって参照される配列の要素を返します*nIndex*します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]

##  <a name="operator_eq"></a>  CSimpleArray::operator =

代入演算子。

```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
コピーする配列。

### <a name="return-value"></a>戻り値

更新されたポインターを返します`CSimpleArray`オブジェクト。

### <a name="remarks"></a>Remarks

すべての要素をコピー、`CSimpleArray`によって参照されるオブジェクト*src*現在の配列オブジェクトに既存のすべてのデータを交換します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]

##  <a name="remove"></a>  CSimpleArray::Remove

配列から指定された要素を削除します。

```
BOOL Remove(const T& t);
```

### <a name="parameters"></a>パラメーター

*t*<br/>
配列から削除する要素。

### <a name="return-value"></a>戻り値

かどうか、要素が見つかったと削除、それ以外の場合は TRUE を返します。

### <a name="remarks"></a>Remarks

要素が削除されると、配列内の残りの要素が空の領域を埋める番号が変更されます。

##  <a name="removeall"></a>  CSimpleArray::RemoveAll

配列からすべての要素を削除します。

```
void RemoveAll();
```

### <a name="remarks"></a>Remarks

配列に現在格納されているすべての要素を削除します。

##  <a name="removeat"></a>  CSimpleArray::RemoveAt

配列から指定した要素を削除します。

```
BOOL RemoveAtint nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
削除する要素を指すインデックスを作成します。

### <a name="return-value"></a>戻り値

要素が削除された、インデックスが有効でなかった場合は FALSE のかどうかは TRUE を返します。

### <a name="remarks"></a>Remarks

要素が削除されると、配列内の残りの要素が空の領域を埋める番号が変更されます。

##  <a name="setatindex"></a>  CSimpleArray::SetAtIndex

配列内の指定した要素を設定します。

```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
変更する要素のインデックス。

*t*<br/>
指定された要素に代入する値。

### <a name="return-value"></a>戻り値

TRUE を返します正常に終了したかどうか、インデックスが無効です。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
