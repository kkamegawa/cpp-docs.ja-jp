---
title: InterfaceTraits 構造体
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
- implements/Microsoft::WRL::Details::InterfaceTraits::IidCount
- implements/Microsoft::WRL::Details::InterfaceTraits::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::InterfaceTraits structure
- Microsoft::WRL::Details::InterfaceTraits::CanCastTo method
- Microsoft::WRL::Details::InterfaceTraits::CastToBase method
- Microsoft::WRL::Details::InterfaceTraits::CastToUnknown method
- Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid method
- Microsoft::WRL::Details::InterfaceTraits::IidCount constant
- Microsoft::WRL::Details::InterfaceTraits::Verify method
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
ms.openlocfilehash: e8222ccaca9572331412b90e696829568eedcf8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386058"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits 構造体

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template<typename I0>
struct __declspec(novtable) InterfaceTraits;

template<typename CloakedType>
struct __declspec(novtable) InterfaceTraits<
    CloakedIid<CloakedType>
>;

template<>
struct __declspec(novtable) InterfaceTraits<Nil>;
```

### <a name="parameters"></a>パラメーター

*I0*<br/>
インターフェイスの名前。

*CloakedType*<br/>
`RuntimeClass`、`Implements`と`ChainInterfaces`、ことができなくなるの一覧で、インターフェイスのインターフェイス Id をサポートします。

## <a name="remarks"></a>Remarks

インターフェイスの一般的な特性を実装します。

2 番目のテンプレートは、クロークされたインターフェイスの特殊化です。 3 番目のテンプレートは、パラメーターが Nil の特殊化です。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック Typedef

名前   | 説明
------ | ------------------------------------------
`Base` | シノニム、 *I0*テンプレート パラメーター。

### <a name="public-methods"></a>パブリック メソッド

名前                                                   | 説明
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[Interfacetraits::cancastto](#cancastto)               | 指定したポインターへのポインターにキャストできるかどうかを示す`Base`します。
[Interfacetraits::casttobase](#casttobase)             | 指定したポインターへのポインターにキャスト`Base`します。
[Interfacetraits::casttounknown](#casttounknown)       | 指定したポインターへのポインターにキャスト`IUnknown`します。
[InterfaceTraits::FillArrayWithIid](#fillarraywithiid) | インターフェイス ID を割り当てます`Base`インデックス引数で指定された配列の要素にします。
[Interfacetraits::verify](#verify)                     | 検証が行われます`Base`は正しく派生します。

### <a name="public-constants"></a>パブリック定数

名前                                   | 説明
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits::IidCount](#iidcount) | インターフェイスに関連付けられた現在の Id の数を保持する`InterfaceTraits`オブジェクト。

## <a name="inheritance-hierarchy"></a>継承階層

`InterfaceTraits`

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::WRL::Details

## <a name="cancastto"></a>Interfacetraits::cancastto

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>パラメーター

*ptr*<br/>
型へのポインターの名前。

*riid*<br/>
インターフェイス ID`Base`します。

*ppv*<br/>
この操作が成功すると場合、 *ppv*で指定されたインターフェイスを指す`Base`します。 それ以外の場合、 *ppv*に設定されている`nullptr`します。

### <a name="return-value"></a>戻り値

**true**この操作が成功した場合と*ptr*へのポインターにキャスト`Base`、それ以外の**false**します。

### <a name="remarks"></a>Remarks

指定したポインターへのポインターにキャストできるかどうかを示す`Base`します。

詳細については`Base`を参照してください、[パブリック Typedef](#public-typedefs)セクション。

## <a name="casttobase"></a>Interfacetraits::casttobase

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
パラメーターの型*ptr*します。

*ptr*<br/>
型へのポインター *T*します。

### <a name="return-value"></a>戻り値

ポインター`Base`します。

### <a name="remarks"></a>Remarks

指定したポインターへのポインターにキャスト`Base`します。

詳細については`Base`を参照してください、[パブリック Typedef](#public-typedefs)セクション。

## <a name="casttounknown"></a>Interfacetraits::casttounknown

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
パラメーターの型*ptr*します。

*ptr*<br/>
型へのポインター *T*します。

### <a name="return-value"></a>戻り値

これから、IUnknown へのポインター`Base`が派生します。

### <a name="remarks"></a>Remarks

指定したポインターへのポインターにキャスト`IUnknown`します。

詳細については`Base`を参照してください、[パブリック Typedef](#public-typedefs)セクション。

## <a name="fillarraywithiid"></a>InterfaceTraits::FillArrayWithIid

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>パラメーター

*index*<br/>
0 から始まるインデックス値を含むフィールドへのポインター。

*iid*<br/>
インターフェイスの Id の配列。

### <a name="remarks"></a>Remarks

インターフェイス ID を割り当てます`Base`インデックス引数で指定された配列の要素にします。

、この API の名前とは対照的に 1 つだけの配列の要素が変更された;全体の配列ではありません。

詳細については`Base`を参照してください、[パブリック Typedef](#public-typedefs)セクション。

## <a name="iidcount"></a>InterfaceTraits::IidCount

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>Remarks

インターフェイスに関連付けられた現在の Id の数を保持する`InterfaceTraits`オブジェクト。

## <a name="verify"></a>Interfacetraits::verify

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>Remarks

検証が行われます`Base`は正しく派生します。

詳細については`Base`を参照してください、[パブリック Typedef](#public-typedefs)セクション。
