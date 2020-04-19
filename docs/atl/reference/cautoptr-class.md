---
title: CAutoPtr クラス
ms.date: 11/04/2016
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
ms.openlocfilehash: 7f4f446aa97f2bf3843b830bd7fb4c4a5d74ffdb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260163"
---
# <a name="cautoptr-class"></a>CAutoPtr クラス

このクラスは、スマート ポインター オブジェクトを表します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <typename T>
class CAutoPtr
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
ポインター型。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAutoPtr::CAutoPtr](#cautoptr)|コンストラクターです。|
|[CAutoPtr:: ~ CAutoPtr](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAutoPtr::Attach](#attach)|既存のポインターの所有権を取得するには、このメソッドを呼び出します。|
|[CAutoPtr::Detach](#detach)|ポインターの所有権を解放するには、このメソッドを呼び出します。|
|[CAutoPtr::Free](#free)|指すオブジェクトを削除するには、このメソッドを呼び出して、`CAutoPtr`します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CAutoPtr::operator T *](#operator_t_star)|キャスト演算子です。|
|[CAutoPtr::operator =](#operator_eq)|代入演算子です。|
|[CAutoPtr::operator -> します。](#operator_ptr)|メンバーへのポインター演算子。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CAutoPtr::m_p](#m_p)|ポインターのデータ メンバー変数です。|

## <a name="remarks"></a>Remarks

このクラスは、作成およびスマート ポインターが含まれ、自動的にスコープ外になったときにリソースを解放して、メモリ リークを防ぐに役立つを管理するためのメソッドを提供します。

さらに、`CAutoPtr`のコピー コンス トラクターと代入演算子所有権を譲渡、ポインターの変換先のポインターにポインターをコピーし、元のポインターを NULL に設定します。 したがって 2 つのことはできません`CAutoPtr`同じのポインターを格納する各オブジェクトし、これにより、2 回、同じポインターを削除する可能性が削減されます。

`CAutoPtr` ポインターのコレクションの作成を簡略化します。 コレクション クラスを派生して、デストラクターをオーバーライド、代わりのコレクションを作成する単純な`CAutoPtr`オブジェクト。 コレクションが削除されたときに、`CAutoPtr`オブジェクトがスコープ外に出るし、自動的に削除されます。

[CHeapPtr](../../atl/reference/cheapptr-class.md)バリアントと同じ方法で作業と`CAutoPtr`割り当てし、C++ ではなく別のヒープ関数を使用してメモリを解放することを除いて、**新しい**と**削除**演算子。 [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)のような`CAutoPtr`、使用されている唯一の違い**new[] をベクター**と**ベクター delete[]** の割り当てし、メモリを解放します。

参照してください[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)と[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)配列またはスマート ポインターのリストが必要な場合。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

## <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

##  <a name="attach"></a>  CAutoPtr::Attach

既存のポインターの所有権を取得するには、このメソッドを呼び出します。

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
`CAutoPtr` This ポインターの所有権を持つオブジェクト。

### <a name="remarks"></a>Remarks

ときに、`CAutoPtr`オブジェクト ポインターの所有権を取得する、自動的に削除されますポインターと割り当てられたデータ スコープ外になったときにします。 場合[CAutoPtr::Detach](#detach)が呼び出されると、プログラマ、もう一度特定のいずれかの解放を担当リソースが割り当てられます。

場合、デバッグ ビルドで、アサーション エラーが発生、 [CAutoPtr::m_p](#m_p)データ メンバーは、現在は既存の値を指します。 つまり、NULL と等しくはありません。

### <a name="example"></a>例

例を参照してください、 [CAutoPtr 概要](../../atl/reference/cautoptr-class.md)します。

##  <a name="cautoptr"></a>  CAutoPtr::CAutoPtr

コンストラクターです。

```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
既存のポインター。

*TSrc*<br/>
別に管理されている型`CAutoPtr`、現在のオブジェクトを初期化するために使用します。

### <a name="remarks"></a>Remarks

`CAutoPtr`オブジェクトの作成は、既存のポインターを使用して、この場合、ポインターの所有権を転送します。

### <a name="example"></a>例

例を参照してください、 [CAutoPtr 概要](../../atl/reference/cautoptr-class.md)します。

##  <a name="dtor"></a>  CAutoPtr:: ~ CAutoPtr

デストラクターです。

```
~CAutoPtr() throw();
```

### <a name="remarks"></a>Remarks

割り当てられたリソースを解放します。 呼び出し[CAutoPtr::Free](#free)します。

##  <a name="detach"></a>  CAutoPtr::Detach

ポインターの所有権を解放するには、このメソッドを呼び出します。

```
T* Detach() throw();
```

### <a name="return-value"></a>戻り値

ポインターのコピーを返します。

### <a name="remarks"></a>Remarks

ポインターの所有権を解放、 [CAutoPtr::m_p](#m_p)に null の場合、データ メンバー変数と、ポインターのコピーを返します。 呼び出した後`Detach`、メモリを解放するには、プログラマの責任割り当てられるリソースを`CAutoPtr`オブジェクトが以前と想定しています reponsibility します。

### <a name="example"></a>例

例を参照してください、 [CAutoPtr 概要](../../atl/reference/cautoptr-class.md)します。

##  <a name="free"></a>  CAutoPtr::Free

指すオブジェクトを削除するには、このメソッドを呼び出して、`CAutoPtr`します。

```
void Free() throw();
```

### <a name="remarks"></a>Remarks

によって指される、オブジェクト、`CAutoPtr`が解放されると、 [CAutoPtr::m_p](#m_p)データ メンバー変数が NULL に設定されます。

##  <a name="m_p"></a>  CAutoPtr::m_p

ポインターのデータ メンバー変数です。

```
T* m_p;
```

### <a name="remarks"></a>Remarks

このメンバー変数は、ポインターの情報を保持します。

##  <a name="operator_eq"></a>  CAutoPtr::operator =

代入演算子です。

```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>パラメーター

*p*<br/>
ポインター。

*TSrc*<br/>
クラスの型。

### <a name="return-value"></a>戻り値

参照を返します、 **CAutoPtr\< T >** します。

### <a name="remarks"></a>Remarks

代入演算子をデタッチします、`CAutoPtr`オブジェクトを現在のポインターから新しいポインターをアタッチします*p*代わりにします。

### <a name="example"></a>例

例を参照してください、 [CAutoPtr 概要](../../atl/reference/cautoptr-class.md)します。

##  <a name="operator_ptr"></a>  CAutoPtr::operator -&gt;

メンバーへのポインター演算子。

```
T* operator->() const throw();
```

### <a name="return-value"></a>戻り値

値を返します、 [CAutoPtr::m_p](#m_p)メンバー変数のデータ。

### <a name="remarks"></a>Remarks

この演算子によって示されるクラスのメソッドを呼び出すを使用して、`CAutoPtr`オブジェクト。 場合、デバッグ ビルドで、アサーション エラーが発生、 `CAutoPtr` NULL を指します。

### <a name="example"></a>例

例を参照してください、 [CAutoPtr 概要](../../atl/reference/cautoptr-class.md)します。

##  <a name="operator_t_star"></a>  CAutoPtr::operator T *

キャスト演算子です。

```
operator T* () const throw();
```

### <a name="return-value"></a>戻り値

クラス テンプレートで定義されたオブジェクト データ型へのポインターを返します。

### <a name="example"></a>例

例を参照してください、 [CAutoPtr 概要](../../atl/reference/cautoptr-class.md)します。

## <a name="see-also"></a>関連項目

[CHeapPtr クラス](../../atl/reference/cheapptr-class.md)<br/>
[CAutoVectorPtr クラス](../../atl/reference/cautovectorptr-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
