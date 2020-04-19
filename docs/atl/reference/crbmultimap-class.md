---
title: CRBMultiMap クラス
ms.date: 11/04/2016
f1_keywords:
- CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::FindFirstWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextValueWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextWithKey
- ATLCOLL/ATL::CRBMultiMap::Insert
- ATLCOLL/ATL::CRBMultiMap::RemoveKey
helpviewer_keywords:
- CRBMultiMap class
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
ms.openlocfilehash: 03a9639e8b0b3d11a414e5db0ce874d7ca8f2d45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278138"
---
# <a name="crbmultimap-class"></a>CRBMultiMap クラス

このクラスは、各キーは、バイナリ レッド ブラック ツリーを使用して、1 つ以上の値を関連付けることにより、マッピング構造体を表します。

## <a name="syntax"></a>構文

```
template<typename K,
         typename V,
         class KTraits = CElementTraits<K>,
         class VTraits = CElementTraits<V>>
class CRBMultiMap : public CRBTree<K, V, KTraits, VTraits>
```

#### <a name="parameters"></a>パラメーター

*K*<br/>
キーの要素の型。

*V*<br/>
要素の値の型。

*KTraits*<br/>
コピーまたは主要な要素を移動するために使用するコードです。 参照してください[CElementTraits クラス](../../atl/reference/celementtraits-class.md)の詳細。

*VTraits*<br/>
コピーまたは値の要素を移動するために使用するコードです。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|コンストラクターです。|
|[CRBMultiMap:: ~ CRBMultiMap](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|指定したキーを持つ最初の要素の位置を検索するには、このメソッドを呼び出します。|
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|指定されたキーに関連付けられている値を取得するには、このメソッドを呼び出すし、位置を表す値を更新します。|
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|指定されたキーに関連付けられている要素を取得するには、このメソッドを呼び出すし、位置を表す値を更新します。|
|[CRBMultiMap::Insert](#insert)|マップに要素のペアを挿入するには、このメソッドを呼び出します。|
|[CRBMultiMap::RemoveKey](#removekey)|指定されたキーのキー/値の要素のすべてを削除するには、このメソッドを呼び出します。|

## <a name="remarks"></a>Remarks

`CRBMultiMap` 要素のキーと値の順序付き配列を管理する特定の型のマッピングの配列のサポートを提供します。 異なり、 [CRBMap](../../atl/reference/crbmap-class.md)クラスでは、各キーが 1 つ以上の値を関連付けることができます。

バイナリ ツリーの要素 (キーと値で構成される) が格納されている構造体を使用して、 [CRBMultiMap::Insert](#insert)メソッド。 使用して要素を削除することができます、 [CRBMultiMap::RemoveKey](#removekey)メソッドで、指定したキーに一致するすべての要素を削除します。

ツリーの走査が可能なメソッドで行ったなど[CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition)、 [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)、および[CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)します。 アクセス、1 つのキー可能性のある複数の値が可能な限りを使用して、 [CRBMultiMap::FindFirstWithKey](#findfirstwithkey)、 [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)、および[CRBMultiMap::GetNextWithKey](#getnextwithkey)メソッド。 例をご覧ください[CRBMultiMap::CRBMultiMap](#crbmultimap)実際には、この図の。

*KTraits*と*VTraits*パラメーターは、特性クラスをコピーまたは要素の移動に必要な補足コードが含まれています。

`CRBMultiMap` 派生[CRBTree](../../atl/reference/crbtree-class.md)、レッド ブラック アルゴリズムを使用してバイナリ ツリーを実装します。 代わりに`CRBMultiMap`と`CRBMap`によって提供される、 [CAtlMap](../../atl/reference/catlmap-class.md)クラス。 格納する要素の数が少ない場合は、使用を検討して、 [CSimpleMap](../../atl/reference/csimplemap-class.md)クラスの代わりにします。

さまざまなコレクション クラスとその機能とパフォーマンス特性の詳細については、次を参照してください。 [ATL コレクション クラス](../../atl/atl-collection-classes.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="crbmultimap"></a>  CRBMultiMap::CRBMultiMap

コンストラクターです。

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>パラメーター

*nBlockSize*<br/>
ブロック サイズ。

### <a name="remarks"></a>Remarks

*NBlockSize*パラメーターは、新しい要素が必要なときに割り当てられたメモリ量の測定単位です。 ブロック サイズの増加はメモリ割り当てルーチンの呼び出しを減らすためがより多くのリソースを使用します。 既定値に、一度に 10 個の要素の領域を割り当てます。

基本クラスのドキュメントを参照して[CRBTree](../../atl/reference/crbtree-class.md)使用できるその他の方法についてはします。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

##  <a name="dtor"></a>  CRBMultiMap::~CRBMultiMap

デストラクターです。

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>Remarks

割り当てられたリソースを解放します。

基本クラスのドキュメントを参照して[CRBTree](../../atl/reference/crbtree-class.md)使用できるその他の方法についてはします。

##  <a name="findfirstwithkey"></a>  CRBMultiMap::FindFirstWithKey

指定したキーを持つ最初の要素の位置を検索するには、このメソッドを呼び出します。

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>パラメーター

*key*<br/>
検索する要素を識別するキーを指定します。

### <a name="return-value"></a>戻り値

キーが見つかった場合、NULL それ以外の場合は、キー/値の最初の要素の位置を返します。

### <a name="remarks"></a>Remarks

内のキーを`CRBMultiMap`1 つまたは複数の関連する値を持つことができます。 このメソッドは、特定のキーに関連付けられている最初の値 (これが、実際、唯一の値には) の位置の値が提供されます。 返される位置の値を使用できます[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)または[CRBMultiMap::GetNextWithKey](#getnextwithkey)値を取得し、位置を更新します。

基本クラスのドキュメントを参照して[CRBTree](../../atl/reference/crbtree-class.md)使用できるその他の方法についてはします。

### <a name="example"></a>例

例をご覧ください[CRBMultiMap::CRBMultiMap](#crbmultimap)します。

##  <a name="getnextvaluewithkey"></a>  CRBMultiMap::GetNextValueWithKey

指定されたキーに関連付けられている値を取得するには、このメソッドを呼び出すし、位置を表す値を更新します。

```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
呼び出しで取得した位置の値[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)または[CRBMultiMap::GetNextWithKey](#getnextwithkey)、または以前の呼び出し`GetNextValueWithKey`します。

*key*<br/>
検索する要素を識別するキーを指定します。

### <a name="return-value"></a>戻り値

指定したキーに関連付けられている要素のペアを返します。

### <a name="remarks"></a>Remarks

位置の値は次のようにキーに関連付けられている次の値に更新されます。 値が存在しない場合は、位置の値が NULL に設定されません。

基本クラスのドキュメントを参照して[CRBTree](../../atl/reference/crbtree-class.md)使用できるその他の方法についてはします。

### <a name="example"></a>例

例をご覧ください[CRBMultiMap::CRBMultiMap](#crbmultimap)します。

##  <a name="getnextwithkey"></a>  CRBMultiMap::GetNextWithKey

指定されたキーに関連付けられている要素を取得するには、このメソッドを呼び出すし、位置を表す値を更新します。

```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
呼び出しで取得した位置の値[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)または[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)、または以前の呼び出し`GetNextWithKey`します。

*key*<br/>
検索する要素を識別するキーを指定します。

### <a name="return-value"></a>戻り値

次を返します[CRBTree::CPair クラス](crbtree-class.md#cpair_class)指定のキーに関連付けられている要素。

### <a name="remarks"></a>Remarks

位置の値は次のようにキーに関連付けられている次の値に更新されます。 値が存在しない場合は、位置の値が NULL に設定されません。

基本クラスのドキュメントを参照して[CRBTree](../../atl/reference/crbtree-class.md)使用できるその他の方法についてはします。

##  <a name="insert"></a>  CRBMultiMap::Insert

マップに要素のペアを挿入するには、このメソッドを呼び出します。

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
追加するキー値、`CRBMultiMap`オブジェクト。

*value*<br/>
追加する値、`CRBMultiMap`オブジェクトに関連付けられている*キー*します。

### <a name="return-value"></a>戻り値

キー/値要素のペアの位置を返します、`CRBMultiMap`オブジェクト。

### <a name="remarks"></a>Remarks

基本クラスのドキュメントを参照して[CRBTree](../../atl/reference/crbtree-class.md)使用できるその他の方法についてはします。

### <a name="example"></a>例

例をご覧ください[CRBMultiMap::CRBMultiMap](#crbmultimap)します。

##  <a name="removekey"></a>  CRBMultiMap::RemoveKey

指定されたキーのキー/値の要素のすべてを削除するには、このメソッドを呼び出します。

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>パラメーター

*key*<br/>
削除する要素を識別するキーを指定します。

### <a name="return-value"></a>戻り値

指定したキーに関連付けられている値の数を返します。

### <a name="remarks"></a>Remarks

`RemoveKey` 一致するキーを持つキー/値の要素をすべて削除*キー*します。

基本クラスのドキュメントを参照して[CRBTree](../../atl/reference/crbtree-class.md)使用できるその他の方法についてはします。

### <a name="example"></a>例

例をご覧ください[CRBMultiMap::CRBMultiMap](#crbmultimap)します。

## <a name="see-also"></a>関連項目

[CRBTree クラス](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap クラス](../../atl/reference/catlmap-class.md)<br/>
[CRBMap クラス](../../atl/reference/crbmap-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
