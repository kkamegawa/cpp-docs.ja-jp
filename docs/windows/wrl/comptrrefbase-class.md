---
title: ComPtrRefBase クラス
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
- client/Microsoft::WRL::Details::ComPtrRefBase::ptr_
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRefBase class
- Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable** operator
- Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown** operator
- Microsoft::WRL::Details::ComPtrRefBase::ptr_ data member
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
ms.openlocfilehash: df4e2aa1ce650fd5b1f04baf2f7c4cd2fb4cff93
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336802"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase クラス

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
A [ComPtr\<T >](comptr-class.md)ことによって表されるだけでなく、インターフェイスから派生した型または型、`ComPtr`します。

## <a name="remarks"></a>Remarks

基本クラスを表します、 [ComPtrRef](comptrref-class.md)クラス。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

名前            | 説明
--------------- | -------------------------------------------------
`InterfaceType` | テンプレート パラメーターの型のシノニム*T*します。

### <a name="public-operators"></a>パブリック演算子

名前                                                                       | 説明
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[Comptrrefbase::operator IInspectable * *](#operator-iinspectable-star-star) | 現在ではキャスト[ptr _](#ptr)をポインターを-、-ポインターのデータ メンバー、`IInspectable`インターフェイス。
[Comptrrefbase::operator IUnknown * *](#operator-iunknown-star-star)         | 現在ではキャスト[ptr _](#ptr)をポインターを-、-ポインターのデータ メンバー、`IUnknown`インターフェイス。

### <a name="protected-data-members"></a>プロテクト データ メンバー

名前                        | 説明
--------------------------- | ----------------------------------------------------------------
[Comptrrefbase::ptr _](#ptr) | 現在のテンプレート パラメーターで指定された型へのポインター。

## <a name="inheritance-hierarchy"></a>継承階層

`ComPtrRefBase`

## <a name="requirements"></a>必要条件

**ヘッダー:** client.h

**名前空間:** Microsoft::WRL::Details

## <a name="operator-iinspectable-star-star"></a>Comptrrefbase::operator IInspectable\* \*演算子

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>Remarks

現在ではキャスト[ptr _](#ptr)をポインターを-、-ポインターのデータ メンバー、`IInspectable`インターフェイス。

場合に、エラーが出力されますが、現在`ComPtrRefBase`から派生していない`IInspectable`。

このキャストは使用可能な場合にのみ`__WRL_CLASSIC_COM__`が定義されています。

## <a name="operator-iunknown-star-star"></a>Comptrrefbase::operator IUnknown * * 演算子

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>Remarks

現在ではキャスト[ptr _](#ptr)をポインターを-、-ポインターのデータ メンバー、`IUnknown`インターフェイス。

場合に、エラーが出力されますが、現在`ComPtrRefBase`から派生していない`IUnknown`。

## <a name="ptr"></a>Comptrrefbase::ptr _

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
T* ptr_;
```

### <a name="remarks"></a>Remarks

現在のテンプレート パラメーターで指定された型へのポインター。 `ptr_` 保護されたデータ メンバーです。
