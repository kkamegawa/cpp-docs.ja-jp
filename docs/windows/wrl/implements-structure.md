---
title: Implements 構造体
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
- implements/Microsoft::WRL::Implements::CanCastTo
- implements/Microsoft::WRL::Implements::CastToUnknown
- implements/Microsoft::WRL::Implements::FillArrayWithIid
- implements/Microsoft::WRL::Implements::IidCount
helpviewer_keywords:
- Microsoft::WRL::Implements structure
- Microsoft::WRL::Implements::CanCastTo method
- Microsoft::WRL::Implements::CastToUnknown method
- Microsoft::WRL::Implements::FillArrayWithIid method
- Microsoft::WRL::Implements::IidCount method
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
ms.openlocfilehash: 63cac6931428644cc5ddec7d87e49007e95e039d
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336602"
---
# <a name="implements-structure"></a>Implements 構造体

実装`QueryInterface`と`GetIid`のインターフェイスで指定します。

## <a name="syntax"></a>構文

```cpp
template <
    typename I0,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct __declspec(novtable) Implements :
    Details::ImplementsHelper<
        RuntimeClassFlags<WinRt>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8, I9
        >::TypeT
    >,
    Details::ImplementsBase;

template <
    int flags,
    typename I0,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8
>
struct __declspec(novtable) Implements<
        RuntimeClassFlags<flags>,
        I0, I1, I2, I3, I4, I5, I6, I7, I8> :
    Details::ImplementsHelper<
        RuntimeClassFlags<flags>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8
        >::TypeT
    >,
    Details::ImplementsBase;
```

### <a name="parameters"></a>パラメーター

*I0*<br/>
0 番目のインターフェイス ID です  (必須)。

*I1*<br/>
1 番目のインターフェイス ID です  (オプション)。

*I2*<br/>
2 番目のインターフェイス ID です  (オプション)。

*I3*<br/>
3 番目のインターフェイス ID です  (オプション)。

*I4*<br/>
4 番目のインターフェイス ID です  (オプション)。

*I5*<br/>
5 番目のインターフェイス ID です  (オプション)。

*I6*<br/>
6 番目のインターフェイス ID です  (オプション)。

*I7*<br/>
7 番目のインターフェイス ID です  (オプション)。

*I8*<br/>
8 番目のインターフェイス ID です  (オプション)。

*I9*<br/>
9 番目のインターフェイス ID です  (オプション)。

*flags*<br/>
クラスの構成フラグです。 1 つまたは複数[RuntimeClassType](runtimeclasstype-enumeration.md)列挙体で指定されている、 [RuntimeClassFlags](runtimeclassflags-structure.md)構造体。

## <a name="remarks"></a>Remarks

指定したインターフェイスの一覧から派生し、実装のヘルパー テンプレート`QueryInterface`と`GetIid`します。

各*I0*を通じて*I9*インターフェイス パラメーターは、いずれかから派生する必要があります`IUnknown`、 `IInspectable`、または[ChainInterfaces](chaininterfaces-structure.md)テンプレート。 *フラグ*のサポートが生成されるかどうかを判別します`IUnknown`または`IInspectable`します。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

| 名前        | 説明                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| `RuntimeClassFlags<WinRt>` と同義。 |

### <a name="protected-methods"></a>プロテクト メソッド

| 名前                                              | 説明                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implements::cancastto](#cancastto)               | 指定したインターフェイスへのポインターを取得します。                                                                    |
| [Implements::casttounknown](#casttounknown)       | 基になるポインターを取得します。`IUnknown`インターフェイス。                                                        |
| [Implements::FillArrayWithIid](#fillarraywithiid) | 指定した配列の要素に現在の 0 番目のテンプレート パラメーターで指定されたインターフェイス ID を挿入します。 |

### <a name="protected-constants"></a>保護されている定数

| 名前                              | 説明                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implements::IidCount](#iidcount) | 実装されたインターフェイス Id の数を保持します。 |

## <a name="inheritance-hierarchy"></a>継承階層

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::wrl

## <a name="cancastto"></a>Implements::cancastto

指定したインターフェイスへのポインターを取得します。

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>パラメーター

*riid*<br/>
インターフェイス ID への参照

*ppv*<br/>
かどうかは成功すると、インターフェイスへのポインターで指定された*riid*します。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、E_NOINTERFACE など、エラーを示す HRESULT。

### <a name="remarks"></a>Remarks

これは、QueryInterface 操作を実行する内部のヘルパー関数です。

## <a name="casttounknown"></a>Implements::casttounknown

基になるポインターを取得します。`IUnknown`インターフェイス。

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>戻り値

この操作は、常に成功し、返された、`IUnknown`ポインター。

### <a name="remarks"></a>Remarks

内部のヘルパー関数です。

## <a name="fillarraywithiid"></a>Implements::FillArrayWithIid

指定した配列の要素に現在の 0 番目のテンプレート パラメーターで指定されたインターフェイス ID を挿入します。

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>パラメーター

*index*<br/>
この操作の開始の配列要素を示す 0 から始まるインデックス。 この操作が完了したら、*インデックス*1 ずつインクリメントされます。

*iid*<br/>
IID 型の配列。

### <a name="remarks"></a>Remarks

内部のヘルパー関数です。

## <a name="iidcount"></a>Implements::IidCount

実装されたインターフェイス Id の数を保持します。

```cpp
static const unsigned long IidCount;
```
