---
title: CAutoVectorPtr クラス
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
ms.openlocfilehash: f614318125f3c6bce4003fee5fb4a945c7c88129
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260384"
---
# <a name="cautovectorptr-class"></a>CAutoVectorPtr クラス

このクラスは、新しいベクトルを使用してスマート ポインター オブジェクトを表し、オペレーターを削除します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<typename T>
class CAutoVectorPtr
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
ポインター型。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|コンストラクターです。|
|[CAutoVectorPtr:: ~ CAutoVectorPtr](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAutoVectorPtr::Allocate](#allocate)|指すオブジェクトの配列に必要なメモリを割り当てるには、このメソッドを呼び出す`CAutoVectorPtr`します。|
|[CAutoVectorPtr::Attach](#attach)|既存のポインターの所有権を取得するには、このメソッドを呼び出します。|
|[CAutoVectorPtr::Detach](#detach)|ポインターの所有権を解放するには、このメソッドを呼び出します。|
|[CAutoVectorPtr::Free](#free)|指すオブジェクトを削除するには、このメソッドを呼び出して、`CAutoVectorPtr`します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CAutoVectorPtr::operator T *](#operator_t__star)|キャスト演算子です。|
|[CAutoVectorPtr::operator =](#operator_eq)|代入演算子です。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CAutoVectorPtr::m_p](#m_p)|ポインターのデータ メンバー変数です。|

## <a name="remarks"></a>Remarks

このクラスは、作成およびスマート ポインターが含まれ、自動的にスコープ外になったときにリソースを解放して、メモリ リークを防ぐに役立つを管理するためのメソッドを提供します。 `CAutoVectorPtr` ような`CAutoPtr`、されていることが唯一の違い`CAutoVectorPtr`を使用して[新しいベクター&#91; &#93; ](../../standard-library/new-operators.md#op_new_arr)と[ベクター delete&#91; &#93; ](../../standard-library/new-operators.md#op_delete_arr)の割り当てし、メモリを解放するにはC++ ではなく**新しい**と**削除**演算子。 参照してください[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)場合のコレクション クラス`CAutoVectorPtr`が必要です。

参照してください[CAutoPtr](../../atl/reference/cautoptr-class.md)スマート ポインター クラスを使用する例についてはします。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="allocate"></a>  CAutoVectorPtr::Allocate

指すオブジェクトの配列に必要なメモリを割り当てるには、このメソッドを呼び出す`CAutoVectorPtr`します。

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>パラメーター

*nElements*<br/>
配列の要素数。

### <a name="return-value"></a>戻り値

失敗した場合にメモリが正常な場合は true を返しますが割り当てられます。

### <a name="remarks"></a>Remarks

場合、デバッグ ビルドで、アサーション エラーが発生、 [CAutoVectorPtr::m_p](#m_p)メンバー変数は、現在は既存の値を指します。 つまり、NULL と等しくはありません。

##  <a name="attach"></a>  CAutoVectorPtr::Attach

既存のポインターの所有権を取得するには、このメソッドを呼び出します。

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
`CAutoVectorPtr` This ポインターの所有権を持つオブジェクト。

### <a name="remarks"></a>Remarks

ときに、`CAutoVectorPtr`オブジェクト ポインターの所有権を取得する、自動的に削除されますポインターと割り当てられたデータ スコープ外になったときにします。 場合[CAutoVectorPtr::Detach](#detach)が呼び出されると、プログラマ、もう一度特定のいずれかの解放を担当リソースが割り当てられます。

場合、デバッグ ビルドで、アサーション エラーが発生、 [CAutoVectorPtr::m_p](#m_p)メンバー変数は、現在は既存の値を指します。 つまり、NULL と等しくはありません。

##  <a name="cautovectorptr"></a>  CAutoVectorPtr::CAutoVectorPtr

コンストラクターです。

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
既存のポインター。

### <a name="remarks"></a>Remarks

`CAutoVectorPtr`オブジェクトの作成は、既存のポインターを使用して、この場合、ポインターの所有権を転送します。

##  <a name="dtor"></a>  CAutoVectorPtr:: ~ CAutoVectorPtr

デストラクターです。

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>Remarks

割り当てられたリソースを解放します。 呼び出し[CAutoVectorPtr::Free](#free)します。

##  <a name="detach"></a>  CAutoVectorPtr::Detach

ポインターの所有権を解放するには、このメソッドを呼び出します。

```
T* Detach() throw();
```

### <a name="return-value"></a>戻り値

ポインターのコピーを返します。

### <a name="remarks"></a>Remarks

ポインターの所有権を解放、 [CAutoVectorPtr::m_p](#m_p)メンバー変数に NULL ポインターのコピーを返します。 呼び出した後`Detach`、メモリを解放するには、プログラマの責任割り当てられるリソースを`CAutoVectorPtr`オブジェクトがある以前責任を負っています。

##  <a name="free"></a>  CAutoVectorPtr::Free

指すオブジェクトを削除するには、このメソッドを呼び出して、`CAutoVectorPtr`します。

```
void Free() throw();
```

### <a name="remarks"></a>Remarks

によって指される、オブジェクト、`CAutoVectorPtr`が解放されると、 [CAutoVectorPtr::m_p](#m_p)メンバー変数が NULL に設定されます。

##  <a name="m_p"></a>  CAutoVectorPtr::m_p

ポインターのデータ メンバー変数です。

```
T* m_p;
```

### <a name="remarks"></a>Remarks

このメンバー変数は、ポインターの情報を保持します。

##  <a name="operator_eq"></a>  CAutoVectorPtr::operator =

代入演算子です。

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
ポインター。

### <a name="return-value"></a>戻り値

参照を返します、 **CAutoVectorPtr\< T >** します。

### <a name="remarks"></a>Remarks

代入演算子をデタッチします、`CAutoVectorPtr`オブジェクトを現在のポインターから新しいポインターをアタッチします*p*代わりにします。

##  <a name="operator_t__star"></a>  CAutoVectorPtr::operator T *

キャスト演算子です。

```
operator T*() const throw();
```

### <a name="remarks"></a>Remarks

クラス テンプレートで定義されたオブジェクト データ型へのポインターを返します。

## <a name="see-also"></a>関連項目

[CAutoPtr クラス](../../atl/reference/cautoptr-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
