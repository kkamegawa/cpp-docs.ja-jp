---
title: ComPtrRef クラス
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::GetAddressOf
- client/Microsoft::WRL::Details::ComPtrRef::operator==
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
- client/Microsoft::WRL::Details::ComPtrRef::operator InterfaceType**
- client/Microsoft::WRL::Details::ComPtrRef::operator*
- client/Microsoft::WRL::Details::ComPtrRef::operator T*
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
- client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRef class
- Microsoft::WRL::Details::ComPtrRef::ComPtrRef, constructor
- Microsoft::WRL::Details::ComPtrRef::GetAddressOf method
- Microsoft::WRL::Details::ComPtrRef::operator== operator
- Microsoft::WRL::Details::ComPtrRef::operator!= operator
- Microsoft::WRL::Details::ComPtrRef::operator InterfaceType** operator
- Microsoft::WRL::Details::ComPtrRef::operator* operator
- Microsoft::WRL::Details::ComPtrRef::operator T* operator
- Microsoft::WRL::Details::ComPtrRef::operator void** operator
- Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf method
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
ms.openlocfilehash: 281e02d85e70a84530e6980d31669a73091448d5
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336618"
---
# <a name="comptrref-class"></a>ComPtrRef クラス

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
A [ComPtr\<T >](comptr-class.md)ことによって表されるだけでなく、インターフェイスから派生した型または型、`ComPtr`します。

## <a name="remarks"></a>Remarks

型のオブジェクトへの参照を表す`ComPtr<T>`します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

名前                               | 説明
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef::ComPtrRef](#comptrref) | 新しいインスタンスを初期化、`ComPtrRef`クラス、指定されたポインター`ComPtrRef`オブジェクト。

### <a name="public-methods"></a>パブリック メソッド

名前                                                         | 説明
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[Comptrref::getaddressof](#getaddressof)                     | 現在によって表されるインターフェイスへのポインターのアドレスを取得`ComPtrRef`オブジェクト。
[ComPtrRef::ReleaseAndGetAddressOf](#releaseandgetaddressof) | 現在の削除`ComPtrRef`オブジェクト、ポインター-に-、- へポインターを返します、インターフェイスによって表される、`ComPtrRef`オブジェクト。

### <a name="public-operators"></a>パブリック演算子

名前                                                                     | 説明
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Comptrref::operator InterfaceType * *](#operator-interfacetype-star-star) | 現在の削除`ComPtrRef`オブジェクト、ポインター-に-、- へポインターを返します、インターフェイスによって表される、`ComPtrRef`オブジェクト。
[Comptrref::operator T *](#operator-t-star)                               | 値を返します、 [ptr _](comptrrefbase-class.md#ptr) ComPtrRef オブジェクトを現在のデータ メンバー。
[Comptrref::operator void * *](#operator-void-star-star)                   | 現在の削除`ComPtrRef`オブジェクト、によって表されるインターフェイスへのポインターをキャスト、`ComPtrRef`オブジェクト、ポインターでへのポインター-として`void`、キャスト ポインターを返します。
[ComPtrRef::operator*](#operator-star)                                   | 現在によって表されるインターフェイスへのポインターを取得します。`ComPtrRef`オブジェクト。
[ComPtrRef::operator==](#operator-equality)                              | 2 つの `ComPtrRef` オブジェクトが等しいかどうかを示します。
[ComPtrRef::operator!=](#operator-inequality)                            | 2 つの `ComPtrRef` オブジェクトが等しくないかどうかを示します。

## <a name="inheritance-hierarchy"></a>継承階層

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>必要条件

**ヘッダー:** client.h

**名前空間:** Microsoft::WRL::Details

## <a name="comptrref"></a>Comptrref::comptrref

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>パラメーター

*ptr*<br/>
別の基になる値`ComPtrRef`オブジェクト。

### <a name="remarks"></a>Remarks

新しいインスタンスを初期化、`ComPtrRef`クラス、指定されたポインター`ComPtrRef`オブジェクト。

## <a name="getaddressof"></a>Comptrref::getaddressof

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>戻り値

現在によって表されるインターフェイスへのポインターのアドレス`ComPtrRef`オブジェクト。

### <a name="remarks"></a>Remarks

現在によって表されるインターフェイスへのポインターのアドレスを取得`ComPtrRef`オブジェクト。

## <a name="operator-equality"></a>Comptrref::operator = =

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>パラメーター

*a*<br/>
`ComPtrRef` オブジェクトへの参照。

*b*<br/>
別の参照`ComPtrRef`オブジェクト、または匿名型へのポインター (`void*`)。

### <a name="return-value"></a>戻り値

最初の演算子と**true**場合オブジェクト *、* がオブジェクトと等しい*b*、それ以外の**false**します。

2 番目と 3 番目の演算子を生成**true**場合オブジェクト *、* と等しい**nullptr**、それ以外の**false**します。

4 番目と 5 番目の演算子を生成**true**場合オブジェクト *、* がオブジェクトと等しい*b*、それ以外の**false**します。

### <a name="remarks"></a>Remarks

2 つの `ComPtrRef` オブジェクトが等しいかどうかを示します。

## <a name="operator-inequality"></a>Comptrref::operator! =

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>パラメーター

*a*<br/>
`ComPtrRef` オブジェクトへの参照。

*b*<br/>
別の参照`ComPtrRef`オブジェクト、または匿名のオブジェクトへのポインター (`void*`)。

### <a name="return-value"></a>戻り値

最初の演算子と**true**場合オブジェクト *、* オブジェクトと等しくない*b*、それ以外の**false**します。

2 番目と 3 番目の演算子を生成**true**場合オブジェクト *、* が等しくない**nullptr**、それ以外の**false**します。

4 番目と 5 番目の演算子を生成**true**場合オブジェクト *、* オブジェクトと等しくない*b*、それ以外の**false**します。

### <a name="remarks"></a>Remarks

2 つの `ComPtrRef` オブジェクトが等しくないかどうかを示します。

## <a name="operator-interfacetype-star-star"></a>Comptrref::operator InterfaceType * *

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>Remarks

現在の削除`ComPtrRef`オブジェクト、ポインター-に-、- へポインターを返します、インターフェイスによって表される、`ComPtrRef`オブジェクト。

## <a name="operator-star"></a>Comptrref::operator *

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>戻り値

現在によって表されるインターフェイスへのポインター`ComPtrRef`オブジェクト。

### <a name="remarks"></a>Remarks

現在によって表されるインターフェイスへのポインターを取得します。`ComPtrRef`オブジェクト。

## <a name="operator-t-star"></a>Comptrref::operator T *

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
operator T*();
```

### <a name="remarks"></a>Remarks

値を返します、 [ptr _](comptrrefbase-class.md#ptr) 、現在のデータ メンバー`ComPtrRef`オブジェクト。

## <a name="operator-void-star-star"></a>Comptrref::operator void\*\*

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
operator void**() const;
```

### <a name="remarks"></a>Remarks

現在の削除`ComPtrRef`オブジェクト、によって表されるインターフェイスへのポインターをキャスト、`ComPtrRef`オブジェクト、ポインターでへのポインター-として`void`、キャスト ポインターを返します。

## <a name="releaseandgetaddressof"></a>ComPtrRef::ReleaseAndGetAddressOf

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>戻り値

表されるインターフェイスへのポインターで、削除された`ComPtrRef`オブジェクト。

### <a name="remarks"></a>Remarks

現在の削除`ComPtrRef`オブジェクト、ポインター-に-、- へポインターを返します、インターフェイスによって表される、`ComPtrRef`オブジェクト。
