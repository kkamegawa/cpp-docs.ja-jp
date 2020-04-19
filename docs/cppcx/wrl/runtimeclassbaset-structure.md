---
title: RuntimeClassBaseT 構造体
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
helpviewer_keywords:
- Microsoft::WRL::Details::RuntimeClassBaseT structure
- Microsoft::WRL::Details::RuntimeClassBaseT::AsIID method
- Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS method
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
ms.openlocfilehash: 5d93b3e86e7ba105a42ccbedbbf44c51ada97bbd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403166"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT 構造体

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template <unsigned int RuntimeClassTypeT>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>パラメーター

*RuntimeClassTypeT*<br/>
1 つまたは複数を指定するフラグのフィールド[RuntimeClassType](runtimeclasstype-enumeration.md)列挙子。

## <a name="remarks"></a>Remarks

ヘルパー メソッドを提供します`QueryInterface`操作とのインターフェイス Id を取得します。

## <a name="members"></a>メンバー

### <a name="protected-methods"></a>プロテクト メソッド

名前                                                         | 説明
------------------------------------------------------------ | -----------------------------------------------------------------------------
[RuntimeClassBaseT::AsIID](#asiid)                           | 指定したインターフェイス ID へのポインターを取得します。
[RuntimeClassBaseT::GetImplementedIIDS](#getimplementediids) | インターフェイスの指定された型で実装されている Id の配列を取得します。

## <a name="inheritance-hierarchy"></a>継承階層

`RuntimeClassBaseT`

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::WRL::Details

## <a name="asiid"></a>RuntimeClassBaseT::AsIID

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
template<typename T>
__forceinline static HRESULT AsIID(
   _In_ T* implements,
   REFIID riid,
   _Deref_out_ void **ppvObject
);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
パラメーターで指定されたインターフェイス ID を実装する型*riid*します。

*implements*<br/>
テンプレート パラメーターで指定された型の変数*T*します。

*riid*<br/>
取得するインターフェイス ID。

*ppvObject*<br/>
ポインター-に-、- へのポインター、インターフェイスがパラメーターで指定されたこの操作が成功した場合は、 *riid*します。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、エラーを示す HRESULT。

### <a name="remarks"></a>Remarks

指定したインターフェイス ID へのポインターを取得します。

## <a name="getimplementediids"></a>Runtimeclassbaset::getimplementediids

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
template<typename T>
__forceinline static HRESULT GetImplementedIIDS(
   _In_ T* implements,
   _Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids
);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
種類、*実装*パラメーター。

*implements*<br/>
パラメーターで指定された型へのポインター *T*します。

*iidCount*<br/>
取得するインターフェイス Id の最大数。

*iid*<br/>
この操作があるインターフェイスの型によって実装された Id の配列では正常に完了する場合*T*します。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、エラーを示す HRESULT。

### <a name="remarks"></a>Remarks

インターフェイスの指定された型で実装されている Id の配列を取得します。
