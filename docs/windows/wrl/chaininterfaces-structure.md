---
title: ChainInterfaces 構造体
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
- implements/Microsoft::WRL::ChainInterfaces::IidCount
- implements/Microsoft::WRL::ChainInterfaces::Verify
helpviewer_keywords:
- Microsoft::WRL::ChainInterfaces structure
- Microsoft::WRL::ChainInterfaces::CanCastTo method
- Microsoft::WRL::ChainInterfaces::CastToUnknown method
- Microsoft::WRL::ChainInterfaces::FillArrayWithIid method
- Microsoft::WRL::ChainInterfaces::IidCount constant
- Microsoft::WRL::ChainInterfaces::Verify method
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
ms.openlocfilehash: 9fd315f017d3dcc9823054ea99e845ec99bc4192
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336610"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces 構造体

一連のインターフェイス ID に適用できる検証および初期化関数を指定します。

## <a name="syntax"></a>構文

```cpp
template <
    typename I0,
    typename I1,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct ChainInterfaces : I0;

template <
    typename DerivedType,
    typename BaseType,
    bool hasImplements,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8,
    typename I9
>
struct ChainInterfaces<
    MixIn<
        DerivedType,
        BaseType,
        hasImplements
    >, I1, I2, I3, I4, I5, I6, I7, I8, I9
>;
```

### <a name="parameters"></a>パラメーター

*I0*<br/>
(必須)インターフェイス ID は 0 です。

*I1*<br/>
(必須)ID 1 のインターフェイスです。

*I2*<br/>
(省略可能)インターフェイス ID 2 です。

*I3*<br/>
(省略可能)インターフェイス ID 3 です。

*I4*<br/>
(省略可能)ID 4 のインターフェイスです。

*I5*<br/>
(省略可能)ID 5 のインターフェイスです。

*I6*<br/>
(省略可能)ID 6 のインターフェイスです。

*I7*<br/>
(省略可能)インターフェイス ID 7 です。

*I8*<br/>
(省略可能)インターフェイス ID 8 です。

*I9*<br/>
(省略可能)インターフェイス ID は 9 です。

*DerivedType*<br/>
派生型。

*BaseType*<br/>
派生型の基本型。

*hasImplements*<br/>
ブール値の場合に**true**、ため使用できません、 [MixIn](mixin-structure.md)構造から派生していないクラスを使用して、[実装](implements-structure.md)構造体。

## <a name="members"></a>メンバー

### <a name="protected-methods"></a>プロテクト メソッド

名前                                                   | 説明
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Chaininterfaces::cancastto](#cancastto)               | 指定されたインターフェイス ID をによって定義された特殊な形式をそれぞれにキャストできるかどうかを示す、`ChainInterface`テンプレート パラメーター。
[Chaininterfaces::casttounknown](#casttounknown)       | によって定義された型のインターフェイス ポインターをキャスト、 *I0*へのポインターをテンプレート パラメーター`IUnknown`します。
[Chaininterfaces::fillarraywithiid](#fillarraywithiid) | ストアで定義されたインターフェイス ID、 *I0*インターフェイス Id の指定した配列内の指定した場所にテンプレート パラメーター。
[Chaininterfaces::verify](#verify)                     | 各インターフェイスは、テンプレート パラメーターで定義されていることを確認します*I0*を通じて*I9*から継承`IUnknown`や`IInspectable`、および*I0*から継承。*I1*を通じて*I9*します。

### <a name="protected-constants"></a>保護されている定数

名前                                   | 説明
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[ChainInterfaces::IidCount](#iidcount) | インターフェイスのテンプレート パラメーターで指定されたインターフェイスに含まれている Id の合計数*I0*を通じて*I9*します。

## <a name="inheritance-hierarchy"></a>継承階層

`I0`

`ChainInterfaces`

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::wrl

## <a name="cancastto"></a>Chaininterfaces::cancastto

指定されたインターフェイス ID を既定以外のテンプレート パラメーターで定義された特殊な形式をそれぞれにキャストできるかどうかを示します。

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>パラメーター

*riid*<br/>
インターフェイス ID。

*ppv*<br/>
正常にキャストされた最後のインターフェイス ID へのポインター。

### <a name="return-value"></a>戻り値

**true**すべてのキャスト操作が成功した場合、それ以外の場合**false**します。

## <a name="casttounknown"></a>Chaininterfaces::casttounknown

によって定義された型のインターフェイス ポインターをキャスト、 *I0*へのポインターをテンプレート パラメーター`IUnknown`します。

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>戻り値

ポインター`IUnknown`します。

## <a name="fillarraywithiid"></a>Chaininterfaces::fillarraywithiid

ストアで定義されたインターフェイス ID、 *I0*インターフェイス Id の指定した配列内の指定した場所にテンプレート パラメーター。

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>パラメーター

*index*<br/>
インデックスへのポインター、 *iid*配列。

*iid*<br/>
インターフェイスの Id の配列。

## <a name="iidcount"></a>ChainInterfaces::IidCount

インターフェイスのテンプレート パラメーターで指定されたインターフェイスに含まれている Id の合計数*I0*を通じて*I9*します。

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>戻り値

インターフェイス Id の合計数。

### <a name="remarks"></a>Remarks

テンプレート パラメーター *I0*と*I1*が必要なパラメーターと*I2*を通じて*I9*は省略可能です。 通常、各インターフェイスの IID の数は、1 になります。

## <a name="verify"></a>Chaininterfaces::verify

各インターフェイスは、テンプレート パラメーターで定義されていることを確認します*I0*を通じて*I9*から継承`IUnknown`や`IInspectable`、および*I0*から継承。*I1*を通じて*I9*します。

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>Remarks

検証操作に失敗した場合、`static_assert`エラーを説明するエラー メッセージを出力します。

テンプレート パラメーター *I0*と*I1*が必要なパラメーターと*I2*を通じて*I9*は省略可能です。
