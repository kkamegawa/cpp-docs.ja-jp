---
title: CRBTree クラス
ms.date: 11/04/2016
f1_keywords:
- CRBTree
- ATLCOLL/ATL::CRBTree
- ATLCOLL/ATL::CRBTree::KINARGTYPE
- ATLCOLL/ATL::CRBTree::KOUTARGTYPE
- ATLCOLL/ATL::CRBTree::VINARGTYPE
- ATLCOLL/ATL::CRBTree::VOUTARGTYPE
- ATLCOLL/ATL::CRBTree::FindFirstKeyAfter
- ATLCOLL/ATL::CRBTree::GetAt
- ATLCOLL/ATL::CRBTree::GetCount
- ATLCOLL/ATL::CRBTree::GetHeadPosition
- ATLCOLL/ATL::CRBTree::GetKeyAt
- ATLCOLL/ATL::CRBTree::GetNext
- ATLCOLL/ATL::CRBTree::GetNextAssoc
- ATLCOLL/ATL::CRBTree::GetNextKey
- ATLCOLL/ATL::CRBTree::GetNextValue
- ATLCOLL/ATL::CRBTree::GetPrev
- ATLCOLL/ATL::CRBTree::GetTailPosition
- ATLCOLL/ATL::CRBTree::GetValueAt
- ATLCOLL/ATL::CRBTree::IsEmpty
- ATLCOLL/ATL::CRBTree::RemoveAll
- ATLCOLL/ATL::CRBTree::RemoveAt
- ATLCOLL/ATL::CRBTree::SetValueAt
helpviewer_keywords:
- CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
ms.openlocfilehash: 59416000eecf4be25746d9dedd86ea2af116087a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278073"
---
# <a name="crbtree-class"></a>CRBTree クラス

このクラスは、作成およびレッド ブラック ツリーを利用するためのメソッドを提供します。

## <a name="syntax"></a>構文

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBTree
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

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|[CRBTree::KINARGTYPE](#kinargtype)|キーが入力引数として渡されるときに使用される型。|
|[CRBTree::KOUTARGTYPE](#koutargtype)|キーが出力引数として返されるときに使用する型。|
|[CRBTree::VINARGTYPE](#vinargtype)|型の値が入力引数として渡されるときに使用します。|
|[CRBTree::VOUTARGTYPE](#voutargtype)|型の値が出力引数として渡されるときに使用します。|

### <a name="public-classes"></a>パブリック クラス

|名前|説明|
|----------|-----------------|
|[CRBTree::CPair クラス](#cpair_class)|キーと値の要素を含むクラスです。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CRBTree:: ~ CRBTree](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)|[次へ] の利用可能なキーを使用する要素の位置を検索するには、このメソッドを呼び出します。|
|[CRBTree::GetAt](#getat)|ツリー内の指定位置に要素を取得するには、このメソッドを呼び出します。|
|[CRBTree::GetCount](#getcount)|ツリー内の要素の数を取得するには、このメソッドを呼び出します。|
|[CRBTree::GetHeadPosition](#getheadposition)|ツリーの先頭の要素の位置を表す値を取得するには、このメソッドを呼び出します。|
|[CRBTree::GetKeyAt](#getkeyat)|ツリー内の指定位置からキーを取得するには、このメソッドを呼び出します。|
|[CRBTree::GetNext](#getnext)|格納されている要素へのポインターを取得するには、このメソッドを呼び出して、`CRBTree`オブジェクトし、次の要素の位置を進めます。|
|[CRBTree::GetNextAssoc](#getnextassoc)|キーと、マップに格納されている要素の値を取得するには、このメソッドを呼び出すし、次の要素の位置を進めます。|
|[CRBTree::GetNextKey](#getnextkey)|ツリー内の要素のキーを取得するには、このメソッドを呼び出すし、次の要素の位置を進めます。|
|[CRBTree::GetNextValue](#getnextvalue)|ツリー内の要素の値を取得するには、このメソッドを呼び出すし、次の要素の位置を進めます。|
|[CRBTree::GetPrev](#getprev)|格納されている要素へのポインターを取得するには、このメソッドを呼び出して、`CRBTree`オブジェクト、および前の要素に位置を更新します。|
|[CRBTree::GetTailPosition](#gettailposition)|ツリーの末尾にある要素の位置を表す値を取得するには、このメソッドを呼び出します。|
|[CRBTree::GetValueAt](#getvalueat)|指定された位置に格納されている値を取得するには、このメソッドを呼び出して、`CRBTree`オブジェクト。|
|[CRBTree::IsEmpty](#isempty)|空のツリー オブジェクトをテストするには、このメソッドを呼び出します。|
|[CRBTree::RemoveAll](#removeall)|すべての要素を削除するには、このメソッドを呼び出して、`CRBTree`オブジェクト。|
|[CRBTree::RemoveAt](#removeat)|指定した位置にある要素を削除するには、このメソッドを呼び出す、`CRBTree`オブジェクト。|
|[CRBTree::SetValueAt](#setvalueat)|指定された位置に格納されている値を変更するには、このメソッドを呼び出す、`CRBTree`オブジェクト。|

## <a name="remarks"></a>Remarks

レッド ブラック ツリーは、余分なを使用するバイナリ検索ツリーの情報が変わらないようにするノードごとのビット「バランス」は、ツリーの高さが過度に大きくなるし、パフォーマンスに影響します。

このテンプレート クラスがによって使用されるように設計[CRBMap](../../atl/reference/crbmap-class.md)と[CRBMultiMap](../../atl/reference/crbmultimap-class.md)します。 これらの派生クラスを作成するメソッドの大部分がによって提供される`CRBTree`します。

さまざまなコレクション クラスとその機能とパフォーマンス特性の詳細については、次を参照してください。 [ATL コレクション クラス](../../atl/atl-collection-classes.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="cpair_class"></a>  CRBTree::CPair クラス

キーと値の要素を含むクラスです。

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Remarks

このクラスは、メソッドによって使用[CRBTree::GetAt](#getat)、 [CRBTree::GetNext](#getnext)、および[CRBTree::GetPrev](#getprev)ツリー構造に格納されているキーと値の要素にアクセスします。

メンバーは次のとおりです。

|||
|-|-|
|`m_key`|重要な要素を格納するデータ メンバー。|
|`m_value`|値の要素を格納するデータ メンバー。|

##  <a name="dtor"></a>  CRBTree:: ~ CRBTree

デストラクターです。

```
~CRBTree() throw();
```

### <a name="remarks"></a>Remarks

割り当てられたリソースを解放します。 呼び出し[CRBTree::RemoveAll](#removeall)をすべての要素を削除します。

##  <a name="findfirstkeyafter"></a>  CRBTree::FindFirstKeyAfter

[次へ] の利用可能なキーを使用する要素の位置を検索するには、このメソッドを呼び出します。

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>パラメーター

*key*<br/>
キーの値。

### <a name="return-value"></a>戻り値

[次へ] の利用可能なキーを使用する要素の位置を表す値を返します。 複数の要素ではありませんがある場合は、NULL が返されます。

### <a name="remarks"></a>Remarks

このメソッドを簡単に位置の値を事前に計算することがなく、ツリーを走査します。

##  <a name="getat"></a>  CRBTree::GetAt

ツリー内の指定位置に要素を取得するには、このメソッドを呼び出します。

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
位置を表す値。

*key*<br/>
キーを受け取る変数です。

*value*<br/>
値を受け取る変数です。

### <a name="return-value"></a>戻り値

最初の 2 つのフォームへのポインターを返す、 [CPair](#cpair_class)します。 3 番目の形式は、キーと指定した位置の値を取得します。

### <a name="remarks"></a>Remarks

位置の値以前を決定できるメソッドの呼び出しなど[CRBTree::GetHeadPosition](#getheadposition)または[CRBTree::GetTailPosition](#gettailposition)します。

場合、デバッグ ビルドで、アサーション エラーが発生*pos*が NULL です。

##  <a name="getcount"></a>  CRBTree::GetCount

ツリー内の要素の数を取得するには、このメソッドを呼び出します。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>戻り値

ツリーに格納されている (各キー/値ペアは 1 つの要素) 要素の数を返します。

##  <a name="getheadposition"></a>  CRBTree::GetHeadPosition

ツリーの先頭の要素の位置を表す値を取得するには、このメソッドを呼び出します。

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>戻り値

ツリーの先頭の要素の位置の値を返します。

### <a name="remarks"></a>Remarks

によって返される値`GetHeadPosition`などのメソッドで使用できる[CRBTree::GetKeyAt](#getkeyat)または[CRBTree::GetNext](#getnext)ツリーを走査し、値を取得します。

##  <a name="getkeyat"></a>  CRBTree::GetKeyAt

ツリー内の指定位置からキーを取得するには、このメソッドを呼び出します。

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
位置を表す値。

### <a name="return-value"></a>戻り値

位置に格納されているキーを返します*pos*ツリー。

### <a name="remarks"></a>Remarks

場合*pos*が有効な位置の値では、結果は予測できません。 場合、デバッグ ビルドで、アサーション エラーが発生*pos*が NULL です。

##  <a name="getnext"></a>  CRBTree::GetNext

格納されている要素へのポインターを取得するには、このメソッドを呼び出して、`CRBTree`オブジェクトし、次の要素の位置を進めます。

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
などのメソッドの前回の呼び出しによって返される位置カウンター [CRBTree::GetHeadPosition](#getheadposition)または[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)します。

### <a name="return-value"></a>戻り値

次のポインターを返します[CPair](#cpair_class)ツリー内の値。

### <a name="remarks"></a>Remarks

*Pos*位置カウンターは各呼び出しの後に更新されます。 取得した要素が、ツリー内の最後の場合*pos* NULL に設定されます。

##  <a name="getnextassoc"></a>  CRBTree::GetNextAssoc

キーと、マップに格納されている要素の値を取得するには、このメソッドを呼び出すし、次の要素の位置を進めます。

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
などのメソッドの前回の呼び出しによって返される位置カウンター [CRBTree::GetHeadPosition](#getheadposition)または[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)します。

*key*<br/>
ツリーのキーの種類を指定するテンプレート パラメーター。

*value*<br/>
ツリーの値の型を指定するテンプレート パラメーター。

### <a name="remarks"></a>Remarks

*Pos*位置カウンターは各呼び出しの後に更新されます。 取得した要素が、ツリー内の最後の場合*pos* NULL に設定されます。

##  <a name="getnextkey"></a>  CRBTree::GetNextKey

ツリー内の要素のキーを取得するには、このメソッドを呼び出すし、次の要素の位置を進めます。

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
などのメソッドの前回の呼び出しによって返される位置カウンター [CRBTree::GetHeadPosition](#getheadposition)または[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)します。

### <a name="return-value"></a>戻り値

ツリーで、[次へ] のキーへの参照を返します。

### <a name="remarks"></a>Remarks

現在の位置のカウンターの更新*pos*します。ツリーにエントリがある場合、位置のカウンターは NULL に設定します。

##  <a name="getnextvalue"></a>  CRBTree::GetNextValue

ツリー内の要素の値を取得するには、このメソッドを呼び出すし、次の要素の位置を進めます。

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
などのメソッドの前回の呼び出しによって返される位置カウンター [CRBTree::GetHeadPosition](#getheadposition)または[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)します。

### <a name="return-value"></a>戻り値

ツリーで、[次へ] の値への参照を返します。

### <a name="remarks"></a>Remarks

現在の位置のカウンターの更新*pos*します。ツリーにエントリがある場合、位置のカウンターは NULL に設定します。

##  <a name="getprev"></a>  CRBTree::GetPrev

格納されている要素へのポインターを取得するには、このメソッドを呼び出して、`CRBTree`オブジェクト、および前の要素に位置を更新します。

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
などのメソッドの前回の呼び出しによって返される位置カウンター [CRBTree::GetHeadPosition](#getheadposition)または[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)します。

### <a name="return-value"></a>戻り値

前のポインターを返します[CPair](#cpair_class)ツリーに格納されている値。

### <a name="remarks"></a>Remarks

現在の位置のカウンターの更新*pos*します。ツリーにエントリがある場合、位置のカウンターは NULL に設定します。

##  <a name="gettailposition"></a>  CRBTree::GetTailPosition

ツリーの末尾にある要素の位置を表す値を取得するには、このメソッドを呼び出します。

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>戻り値

ツリーの末尾にある要素の位置の値を返します。

### <a name="remarks"></a>Remarks

によって返される値`GetTailPosition`などのメソッドで使用できる[CRBTree::GetKeyAt](#getkeyat)または[CRBTree::GetPrev](#getprev)ツリーを走査し、値を取得します。

##  <a name="getvalueat"></a>  CRBTree::GetValueAt

指定された位置に格納されている値を取得するには、このメソッドを呼び出して、`CRBTree`オブジェクト。

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
などのメソッドの前回の呼び出しによって返される位置カウンター [CRBTree::GetHeadPosition](#getheadposition)または[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)します。

### <a name="return-value"></a>戻り値

指定された位置に格納されている値への参照を返します、`CRBTree`オブジェクト。

##  <a name="isempty"></a>  CRBTree::IsEmpty

空のツリー オブジェクトをテストするには、このメソッドを呼び出します。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>戻り値

ツリーが空のかどうか、FALSE それ以外の場合は TRUE を返します。

##  <a name="kinargtype"></a>  CRBTree::KINARGTYPE

キーが入力引数として渡されるときに使用される型。

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

##  <a name="koutargtype"></a>  CRBTree::KOUTARGTYPE

キーが出力引数として返されるときに使用する型。

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

##  <a name="removeall"></a>  CRBTree::RemoveAll

すべての要素を削除するには、このメソッドを呼び出して、`CRBTree`オブジェクト。

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Remarks

消去、`CRBTree`要素を格納するために使用するメモリを解放するオブジェクト。

##  <a name="removeat"></a>  CRBTree::RemoveAt

指定した位置にある要素を削除するには、このメソッドを呼び出す、`CRBTree`オブジェクト。

```
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
などのメソッドの前回の呼び出しによって返される位置カウンター [CRBTree::GetHeadPosition](#getheadposition)または[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)します。

### <a name="remarks"></a>Remarks

指定した位置に格納されているキー/値ペアを削除します。 要素の格納に使用されるメモリは解放されます。 によって参照される位置*pos* 、無効になり、ツリー内の他の要素の位置が有効では必ずしも同じ順序を保持します。

##  <a name="setvalueat"></a>  CRBTree::SetValueAt

指定された位置に格納されている値を変更するには、このメソッドを呼び出す、`CRBTree`オブジェクト。

```
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
などのメソッドの前回の呼び出しによって返される位置カウンター [CRBTree::GetHeadPosition](#getheadposition)または[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)します。

*value*<br/>
追加する値、`CRBTree`オブジェクト。

### <a name="remarks"></a>Remarks

指定された位置に格納されている値を変更、`CRBTree`オブジェクト。

##  <a name="vinargtype"></a>  CRBTree::VINARGTYPE

型の値が入力引数として渡されるときに使用します。

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

##  <a name="voutargtype"></a>  CRBTree::VOUTARGTYPE

型の値が出力引数として渡されるときに使用します。

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
