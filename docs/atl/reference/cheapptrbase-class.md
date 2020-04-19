---
title: CHeapPtrBase クラス
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
ms.openlocfilehash: 558c9bd78257a06e123d47a0110375e7f448f90d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245609"
---
# <a name="cheapptrbase-class"></a>CHeapPtrBase クラス

このクラスは、いくつかのヒープのスマート ポインター クラスの基礎を形成します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class T, class Allocator = CCRTAllocator>
class CHeapPtrBase
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
ヒープに格納されるオブジェクトの種類。

*アロケーター*<br/>
メモリの割り当ては、使用するクラス。 既定では、CRT ルーチンは割り当てし、メモリの解放に使用されます。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CHeapPtrBase:: ~ CHeapPtrBase](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|メモリを割り当てるには、このメソッドを呼び出します。|
|[CHeapPtrBase::Attach](#attach)|既存のポインターの所有権を取得するには、このメソッドを呼び出します。|
|[CHeapPtrBase::Detach](#detach)|ポインターの所有権を解放するには、このメソッドを呼び出します。|
|[CHeapPtrBase::Free](#free)|指すオブジェクトを削除するには、このメソッドを呼び出して、`CHeapPtrBase`します。|
|[CHeapPtrBase::ReallocateBytes](#reallocatebytes)|メモリを再割り当てするには、このメソッドを呼び出します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CHeapPtrBase::operator T *](#operator_t_star)|キャスト演算子です。|
|[CHeapPtrBase::operator (& a)](#operator_amp)|& 演算子。|
|[CHeapPtrBase::operator -> します。](#operator_ptr)|メンバーへのポインター演算子。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CHeapPtrBase::m_pData](#m_pdata)|ポインターのデータ メンバー変数です。|

## <a name="remarks"></a>Remarks

このクラスは、いくつかのヒープのスマート ポインター クラスの基礎を形成します。 たとえば、派生クラス[CHeapPtr](../../atl/reference/cheapptr-class.md)と[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)、独自のコンス トラクターと演算子を追加します。 これらのクラスの実装例を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcore.h

##  <a name="allocatebytes"></a>  CHeapPtrBase::AllocateBytes

メモリを割り当てるには、このメソッドを呼び出します。

```
bool AllocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>パラメーター

*nBytes*<br/>
割り当てるメモリのバイト数。

### <a name="return-value"></a>戻り値

True を返します、メモリが正常に割り当てられたそれ以外の場合。

### <a name="remarks"></a>Remarks

場合、デバッグ ビルドで、アサーション エラーが発生、 [CHeapPtrBase::m_pData](#m_pdata)メンバー変数は、現在は既存の値を指します。 つまり、NULL と等しくはありません。

##  <a name="attach"></a>  CHeapPtrBase::Attach

既存のポインターの所有権を取得するには、このメソッドを呼び出します。

```
void Attach(T* pData) throw();
```

### <a name="parameters"></a>パラメーター

*pData*<br/>
`CHeapPtrBase` This ポインターの所有権を持つオブジェクト。

### <a name="remarks"></a>Remarks

ときに、`CHeapPtrBase`オブジェクト ポインターの所有権を取得する、自動的に削除されますポインターと割り当てられたデータ スコープ外になったときにします。

場合、デバッグ ビルドで、アサーション エラーが発生、 [CHeapPtrBase::m_pData](#m_pdata)メンバー変数は、現在は既存の値を指します。 つまり、NULL と等しくはありません。

##  <a name="dtor"></a>  CHeapPtrBase::~CHeapPtrBase

デストラクターです。

```
~CHeapPtrBase() throw();
```

### <a name="remarks"></a>Remarks

割り当てられているすべてのリソースを解放します。

##  <a name="detach"></a>  CHeapPtrBase::Detach

ポインターの所有権を解放するには、このメソッドを呼び出します。

```
T* Detach() throw();
```

### <a name="return-value"></a>戻り値

ポインターのコピーを返します。

### <a name="remarks"></a>Remarks

ポインターの所有権を解放、 [CHeapPtrBase::m_pData](#m_pdata)メンバー変数に NULL ポインターのコピーを返します。

##  <a name="free"></a>  CHeapPtrBase::Free

指すオブジェクトを削除するには、このメソッドを呼び出して、`CHeapPtrBase`します。

```
void Free() throw();
```

### <a name="remarks"></a>Remarks

によって指される、オブジェクト、`CHeapPtrBase`が解放されると、 [CHeapPtrBase::m_pData](#m_pdata)メンバー変数が NULL に設定されます。

##  <a name="m_pdata"></a>  CHeapPtrBase::m_pData

ポインターのデータ メンバー変数です。

```
T* m_pData;
```

### <a name="remarks"></a>Remarks

このメンバー変数は、ポインターの情報を保持します。

##  <a name="operator_amp"></a>  CHeapPtrBase::operator &amp;

& 演算子。

```
T** operator&() throw();
```

### <a name="return-value"></a>戻り値

指すオブジェクトのアドレスを返して、`CHeapPtrBase`オブジェクト。

##  <a name="operator_ptr"></a>  CHeapPtrBase::operator -&gt;

メンバーへのポインター演算子。

```
T* operator->() const throw();
```

### <a name="return-value"></a>戻り値

値を返します、 [CHeapPtrBase::m_pData](#m_pdata)メンバー変数。

### <a name="remarks"></a>Remarks

この演算子によって示されるクラスのメソッドを呼び出すを使用して、`CHeapPtrBase`オブジェクト。 場合、デバッグ ビルドで、アサーション エラーが発生、 `CHeapPtrBase` NULL を指します。

##  <a name="operator_t_star"></a>  CHeapPtrBase::operator T *

キャスト演算子です。

```
operator T*() const throw();
```

### <a name="remarks"></a>Remarks

返します[CHeapPtrBase::m_pData](#m_pdata)します。

##  <a name="reallocatebytes"></a>  CHeapPtrBase::ReallocateBytes

メモリを再割り当てするには、このメソッドを呼び出します。

```
bool ReallocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>パラメーター

*nBytes*<br/>
新しいバイトで、割り当てるメモリ量。

### <a name="return-value"></a>戻り値

True を返します、メモリが正常に割り当てられたそれ以外の場合。

## <a name="see-also"></a>関連項目

[CHeapPtr クラス](../../atl/reference/cheapptr-class.md)<br/>
[CComHeapPtr クラス](../../atl/reference/ccomheapptr-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
