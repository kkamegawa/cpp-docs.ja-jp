---
title: CAtlArray クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlArray
- ATLCOLL/ATL::CAtlArray
- ATLCOLL/ATL::Add
- ATLCOLL/ATL::Append
- ATLCOLL/ATL::AssertValid
- ATLCOLL/ATL::Copy
- ATLCOLL/ATL::FreeExtra
- ATLCOLL/ATL::GetAt
- ATLCOLL/ATL::GetCount
- ATLCOLL/ATL::GetData
- ATLCOLL/ATL::InsertArrayAt
- ATLCOLL/ATL::InsertAt
- ATLCOLL/ATL::IsEmpty
- ATLCOLL/ATL::RemoveAll
- ATLCOLL/ATL::RemoveAt
- ATLCOLL/ATL::SetAt
- ATLCOLL/ATL::SetAtGrow
- ATLCOLL/ATL::SetCount
- ATLCOLL/ATL::INARGTYPE
- ATLCOLL/ATL::OUTARGTYPE
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
ms.openlocfilehash: 6a0b83f722d1b616e9c10713646d337f9cb090a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260845"
---
# <a name="catlarray-class"></a>CAtlArray クラス

このクラスは、配列オブジェクトを実装します。

## <a name="syntax"></a>構文

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>パラメーター

*E*<br/>
配列に格納されるデータの型。

*ETraits*<br/>
コピーまたは要素を移動するために使用するコードです。

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[[追加]](#add)|配列オブジェクトに要素を追加するには、このメソッドを呼び出します。|
|[追加](#append)|1 つの配列の内容を別の末尾に追加するには、このメソッドを呼び出します。|
|[AssertValid](#assertvalid)|配列のオブジェクトが有効であることを確認するには、このメソッドを呼び出します。|
|[CAtlArray](#catlarray)|コンストラクターです。|
|[~ CAtlArray](#dtor)|デストラクターです。|
|[コピー](#copy)|1 つの配列の要素をコピーするには、このメソッドを呼び出します。|
|[FreeExtra](#freeextra)|配列から空の要素を削除するには、このメソッドを呼び出します。|
|[GetAt](#getat)|配列オブジェクトから 1 つの要素を取得するには、このメソッドを呼び出します。|
|[GetCount](#getcount)|配列に格納されている要素の数を返すには、このメソッドを呼び出します。|
|[GetData](#getdata)|配列の最初の要素へのポインターを返すには、このメソッドを呼び出します。|
|[InsertArrayAt](#insertarrayat)|別に 1 つの配列を挿入するには、このメソッドを呼び出します。|
|[InsertAt](#insertat)|配列オブジェクトには、新しい要素 (または要素の複数のコピー) を挿入するには、このメソッドを呼び出します。|
|[IsEmpty](#isempty)|配列が空の場合をテストするには、このメソッドを呼び出します。|
|[RemoveAll](#removeall)|配列オブジェクトからすべての要素を削除するには、このメソッドを呼び出します。|
|[RemoveAt](#removeat)|配列から 1 つまたは複数の要素を削除するには、このメソッドを呼び出します。|
|[SetAt](#setat)|配列オブジェクトに要素の値を設定するには、このメソッドを呼び出します。|
|[SetAtGrow](#setatgrow)|必要に応じて、配列を展開する、配列オブジェクトに要素の値を設定するには、このメソッドを呼び出します。|
|[SetCount](#setcount)|配列オブジェクトのサイズを設定するには、このメソッドを呼び出します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[演算子&#91;&#93;](#operator_at)|配列の要素への参照を返すには、この演算子を呼び出します。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[INARGTYPE](#inargtype)|配列に要素を追加するために使用するデータ型。|
|[OUTARGTYPE](#outargtype)|配列から要素を取得するために使用するデータ型。|

## <a name="remarks"></a>Remarks

`CAtlArray` 作成およびユーザー定義型の要素の配列を管理するためのメソッドを提供します。 標準の c 言語の配列に似ていますが、`CAtlArray`オブジェクトを動的に縮小および必要に応じて大きくなります。 配列インデックスが常に 0 の位置から開始し、上限の修正、または新しい要素が追加されると展開を許可されていることができます。

ATL クラスの要素の数が少ない配列[CSimpleArray](../../atl/reference/csimplearray-class.md)ことができます。

`CAtlArray` mfc の関連性が高い`CArray`クラスをシリアル化をサポートしていないものの、MFC プロジェクトで動作します。

詳細については、次を参照してください。 [ATL コレクション クラス](../../atl/atl-collection-classes.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="add"></a>  CAtlArray::Add

配列オブジェクトに要素を追加するには、このメソッドを呼び出します。

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>パラメーター

*要素*<br/>
配列に追加する要素。

### <a name="return-value"></a>戻り値

追加された要素のインデックスを返します。

### <a name="remarks"></a>Remarks

新しい要素は、配列の末尾に追加されます。 要素が指定されない場合、空の要素が追加されます。つまり、実際の要素が追加されても、サイズの配列が向上します。 操作が失敗した場合、 [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)は E_OUTOFMEMORY 引数で呼び出されます。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

##  <a name="append"></a>  CAtlArray::Append

1 つの配列の内容を別の末尾に追加するには、このメソッドを呼び出します。

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>パラメーター

*aSrc*<br/>
追加先の配列。

### <a name="return-value"></a>戻り値

追加された最初の要素のインデックスを返します。

### <a name="remarks"></a>Remarks

指定した配列内の要素は、既存の配列の末尾に追加されます。 必要に応じては、新しい要素に対応するメモリが割り当てられます。

配列自体に追加することはできませんし、同じ型の配列があります。

デバッグ ビルドは atlassert 場合、`CAtlArray`引数が有効な配列ではない場合*aSrc*は同じオブジェクトを参照します。 リリース ビルドで無効な引数が予期しない動作にあります。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

##  <a name="assertvalid"></a>  CAtlArray::AssertValid

配列のオブジェクトが有効であることを確認するには、このメソッドを呼び出します。

```
void AssertValid() const;
```

### <a name="remarks"></a>Remarks

配列のオブジェクトが有効でない場合、アサーションが ATLASSERT にスローされます。 このメソッドは _DEBUG が定義されている場合にのみ使用できます。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

##  <a name="catlarray"></a>  CAtlArray::CAtlArray

コンストラクターです。

```
CAtlArray() throw();
```

### <a name="remarks"></a>Remarks

配列オブジェクトを初期化します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

##  <a name="dtor"></a>  CAtlArray::~CAtlArray

デストラクターです。

```
~CAtlArray() throw();
```

### <a name="remarks"></a>Remarks

配列オブジェクトによって使用されているリソースを解放します。

##  <a name="copy"></a>  CAtlArray::Copy

1 つの配列の要素をコピーするには、このメソッドを呼び出します。

```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>パラメーター

*aSrc*<br/>
配列にコピーする要素のソース。

### <a name="remarks"></a>Remarks

別の配列の要素を含む 1 つの配列の要素を上書きするには、このメソッドを呼び出します。 必要に応じては、新しい要素に対応するメモリが割り当てられます。 場合によっては、自身に配列の要素をコピーすることはできません。

配列の既存の内容を保持する場合を使用して、 [CAtlArray::Append](#append)代わりにします。

デバッグ ビルドで ATLASSERT が発生します。 既存の`CAtlArray`オブジェクトが有効でない場合、または*aSrc*は同じオブジェクトを参照します。 リリース ビルドで無効な引数が予期しない動作にあります。

> [!NOTE]
> `CAtlArray::Copy` 作成された要素から成る配列をサポートしていません、 [CAutoPtr](../../atl/reference/cautoptr-class.md)クラス。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

##  <a name="freeextra"></a>  CAtlArray::FreeExtra

配列から空の要素を削除するには、このメソッドを呼び出します。

```
void FreeExtra() throw();
```

### <a name="remarks"></a>Remarks

空の要素が削除されますが、サイズと配列の上限は変更されません。

デバッグ ビルドでは CAtlArray オブジェクトが有効でない場合、または配列の最大サイズを超える場合、atlassert されます。

##  <a name="getat"></a>  CAtlArray::GetAt

呼び出しには、このメソッドは、配列オブジェクトから 1 つの要素を取得します。

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>パラメーター

*iElement*<br/>
返される配列要素のインデックス値。

### <a name="return-value"></a>戻り値

必要な配列の要素への参照を返します。

### <a name="remarks"></a>Remarks

デバッグ ビルドは atlassert 場合*iElement*配列の要素の数を超えています。 リリース ビルドで無効な引数が予期しない動作にあります。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

##  <a name="getcount"></a>  CAtlArray::GetCount

配列に格納されている要素の数を返すには、このメソッドを呼び出します。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>戻り値

配列に格納されている要素の数を返します。

### <a name="remarks"></a>Remarks

値がによって返される配列の最初の要素が 0 の位置は、`GetCount`が常に 1 より大きいインデックスの最大値。

### <a name="example"></a>例

例をご覧ください[CAtlArray::GetAt](#getat)します。

##  <a name="getdata"></a>  CAtlArray::GetData

配列の最初の要素へのポインターを返すには、このメソッドを呼び出します。

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>戻り値

配列内の最初の要素を格納するメモリ位置へのポインターを返します。 使用可能な要素が存在しない場合は、NULL が返されます。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

##  <a name="inargtype"></a>  CAtlArray::INARGTYPE

配列に要素を追加するために使用するデータ型。

```
typedef ETraits::INARGTYPE INARGTYPE;
```

##  <a name="insertarrayat"></a>  CAtlArray::InsertArrayAt

別に 1 つの配列を挿入するには、このメソッドを呼び出します。

```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>パラメーター

*iStart*<br/>
配列が挿入されるインデックス。

*paNew*<br/>
挿入先の配列。

### <a name="remarks"></a>Remarks

要素を配列から*paNew*要素で始まる配列オブジェクトにコピーされます*iStart*します。 既存の配列要素は、上書きを回避するために移動されます。

場合、デバッグ ビルドで ATLASSERT が発生する、`CAtlArray`オブジェクトが有効でない場合は、 *paNew*ポインターが NULL または無効です。

> [!NOTE]
> `CAtlArray::InsertArrayAt` 作成された要素から成る配列をサポートしていません、 [CAutoPtr](../../atl/reference/cautoptr-class.md)クラス。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

##  <a name="insertat"></a>  CAtlArray::InsertAt

配列オブジェクトには、新しい要素 (または要素の複数のコピー) を挿入するには、このメソッドを呼び出します。

```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>パラメーター

*iElement*<br/>
要素または要素が挿入されるインデックス。

*要素*<br/>
要素または挿入する要素の値。

*nCount*<br/>
追加する要素の数。

### <a name="remarks"></a>Remarks

開始インデックス位置として、配列に 1 つまたは複数の要素を挿入*iElement*します。 既存の要素は、上書きを回避するために移動されます。

デバッグ ビルドは atlassert 場合、`CAtlArray`オブジェクトが無効、追加する要素の数が 0 の場合、または格納する配列の要素の合計数が大きすぎます。 製品版ビルドでは、無効なパラメーターを渡すと、予期しない結果が発生する可能性があります。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

##  <a name="isempty"></a>  CAtlArray::IsEmpty

配列が空の場合をテストするには、このメソッドを呼び出します。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>戻り値

配列が false でそれ以外の場合、空の場合は true を返します。

### <a name="remarks"></a>Remarks

配列は要素が含まれていない場合は空にすることはできます。 そのため、配列に空の要素が含まれている場合でも空ではないです。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

##  <a name="operator_at"></a>  CAtlArray::operator []

配列の要素への参照を返すには、この演算子を呼び出します。

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>パラメーター

*iElement*<br/>
返される配列要素のインデックス値。

### <a name="return-value"></a>戻り値

必要な配列の要素への参照を返します。

### <a name="remarks"></a>Remarks

同様の機能を実行します[CAtlArray::GetAt](#getat)します。 MFC クラスとは異なり[CArray](../../mfc/reference/carray-class.md)、代わりにこの演算子は使用できません[CAtlArray::SetAt](#setat)します。

デバッグ ビルドは atlassert 場合*iElement*配列の要素の合計数を超えています。 製品版ビルドでは、予期しない結果が無効なパラメーターにあります。

##  <a name="outargtype"></a>  CAtlArray::OUTARGTYPE

配列から要素を取得するために使用するデータ型。

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

##  <a name="removeall"></a>  CAtlArray::RemoveAll

配列オブジェクトからすべての要素を削除するには、このメソッドを呼び出します。

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Remarks

配列オブジェクトからすべての要素を削除します。

このメソッドを呼び出す[CAtlArray::SetCount](#setcount)配列のサイズを変更して、その後、割り当てられたメモリを解放します。

### <a name="example"></a>例

例をご覧ください[CAtlArray::IsEmpty](#isempty)します。

##  <a name="removeat"></a>  CAtlArray::RemoveAt

配列から 1 つまたは複数の要素を削除するには、このメソッドを呼び出します。

```
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>パラメーター

*iElement*<br/>
削除する最初の要素のインデックス。

*nCount*<br/>
削除する要素の数を指定します。

### <a name="remarks"></a>Remarks

配列から 1 つまたは複数の要素を削除します。 残りの要素は下に移動します。 上限は、デクリメントですがへの呼び出しまでメモリは解放されません[CAtlArray::FreeExtra](#freeextra)されます。

場合、デバッグ ビルドで ATLASSERT が発生する、`CAtlArray`オブジェクトが有効でない場合の合計*iElement*と*nCount*配列の要素の合計数を超えています。 製品版ビルドでは、予期しない結果が無効なパラメーターにあります。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

##  <a name="setat"></a>  CAtlArray::SetAt

配列オブジェクトに要素の値を設定するには、このメソッドを呼び出します。

```
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>パラメーター

*iElement*<br/>
設定する配列要素を指すインデックス。

*要素*<br/>
指定した要素の新しい値。

### <a name="remarks"></a>Remarks

デバッグ ビルドは atlassert 場合*iElement*配列の要素の数を超えています。 製品版ビルドで予期しない結果に無効なパラメーターがあります。

### <a name="example"></a>例

例をご覧ください[CAtlArray::GetAt](#getat)します。

##  <a name="setcount"></a>  CAtlArray::SetCount

配列オブジェクトのサイズを設定するには、このメソッドを呼び出します。

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>パラメーター

*nNewSize*<br/>
配列の必要なサイズ。

*nGrowBy*<br/>
値を決定するために使用するバッファー。 値-1 の場合、使用する計算を内部的の値。

### <a name="return-value"></a>戻り値

場合は、配列サイズ変更が正常に、それ以外の場合は true を返します。

### <a name="remarks"></a>Remarks

配列の増加またはサイズは縮小できます。 増やすことがある場合は、空の要素が配列に追加されます。 低下している場合は、最大のインデックスを持つ要素が削除され、メモリを解放します。

このメソッドを使用すると、使用する前に、配列のサイズを設定できます。 場合`SetCount`が使用されていない要素を追加するプロセス-実行される後続のメモリ割り当てと -はパフォーマンスが低下して、メモリが断片化します。

### <a name="example"></a>例

例をご覧ください[CAtlArray::GetData](#getdata)します。

##  <a name="setatgrow"></a>  CAtlArray::SetAtGrow

必要に応じて、配列を展開する、配列オブジェクトに要素の値を設定するには、このメソッドを呼び出します。

```
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>パラメーター

*iElement*<br/>
設定する配列要素を指すインデックス。

*要素*<br/>
指定した要素の新しい値。

### <a name="remarks"></a>Remarks

インデックスが指す要素の値に置き換えます。 場合*iElement*が現在のサイズより大きい、配列の配列は自動的に増加への呼び出しを使用して[CAtlArray::SetCount](#setcount)します。 デバッグ ビルドは atlassert 場合、`CAtlArray`オブジェクトが無効です。 製品版ビルドでは、予期しない結果が無効なパラメーターにあります。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>関連項目

[MMXSwarm サンプル](../../overview/visual-cpp-samples.md)<br/>
[DynamicConsumer サンプル](../../overview/visual-cpp-samples.md)<br/>
[UpdatePV サンプル](../../overview/visual-cpp-samples.md)<br/>
[マーキーのサンプル](../../overview/visual-cpp-samples.md)<br/>
[CArray クラス](../../mfc/reference/carray-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
