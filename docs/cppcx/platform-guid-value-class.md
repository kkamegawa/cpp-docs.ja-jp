---
title: Platform::Guid 値クラス
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: ad71ed4965a3dd4846c9ba5d8ed2627ed8f7e056
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334652"
---
# <a name="platformguid-value-class"></a>Platform::Guid 値クラス

[GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931) の種類を、Windows ランタイムの型システムで表します。

## <a name="syntax"></a>構文

```cpp
public value struct Guid
```

### <a name="members"></a>メンバー

`Platform::Guid` `Equals()`、`GetHashCode()`と`ToString()`から派生したメソッド、 [platform::object Class](../cppcx/platform-object-class.md)、および`GetTypeCode()`から派生したメソッド、 [platform::type Class](../cppcx/platform-type-class.md)します。 `Platform::Guid` 次のメンバーがあります。

|メンバー|説明|
|------------|-----------------|
|[Guid](#ctor)|`Platform::Guid` の新しいインスタンスを初期化します。|
|[operator==](#operator-equality)|等値演算子。|
|[operator!=](#operator-inequality)|非等値演算子。|
|[operator&lt;](#operator-less)|小なり演算子。|
|[演算子 ()](#operator-call)|`Platform::Guid` を `GUID`に変換します。|

### <a name="remarks"></a>Remarks

新しいを生成する方法の例については`Platform::Guid`Windows 関数を使用して[CoCreateGuid](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateguid)を参照してください[WinRT コンポーネント。GUID を生成する方法は?](https://www.eternalcoding.com/?p=383)

### <a name="requirements"></a>必要条件

**最小値には、クライアントがサポートされています。** Windows 8

**最小値には、サーバーがサポートされています。** Windows Server 2012

**名前空間:** プラットフォーム

**メタデータ:** platform.winmd

## <a name="ctor"></a> Guid::guid コンス トラクター

`Platform::Guid` の新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    unsigned char d,
    unsigned char e,
    unsigned char f,
    unsigned char g,
    unsigned char h,
    unsigned char i,
    unsigned char j,
    unsigned char k );

Guid(GUID m);

Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    Array<unsigned char>^ n );
```

### <a name="parameters"></a>パラメーター

*a*<br/>
最初の 4 バイト、`GUID`します。

*b*<br/>
次の 2 バイト、`GUID`します。

*c*<br/>
次の 2 バイト、`GUID`します。

*d*<br/>
次のバイト、`GUID`します。

*e*<br/>
次のバイト、`GUID`します。

*f*<br/>
次のバイト、`GUID`します。

*g*<br/>
次のバイト、`GUID`します。

*h*<br/>
次のバイト、`GUID`します。

*i*<br/>
次のバイト、`GUID`します。

*j*<br/>
次のバイト、`GUID`します。

*k*<br/>
次のバイト、`GUID`します。

*m*<br/>
A`GUID`形式で、 [GUID 構造体](https://msdn.microsoft.com/library/windows/desktop/aa373931)します。

*n*<br/>
残りの 8 バイト、`GUID`します。

## <a name="operator-equality"></a> Guid::operator 演算子 = =

2 つの `Platform::Guid` インスタンスを比較し、相互に等価かどうかを判断します。

### <a name="syntax"></a>構文

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>パラメーター

*guid1*<br/>
比較対象となる最初の `Platform::Guid`。

*guid2*<br/>
比較対象となる 2 番目の `Platform::Guid`。

### <a name="return-value"></a>戻り値

True の場合、2 つ`Platform::Guid`インスタンスが等しい。

## <a name="operator-inequality"></a> Guid::operator! = 演算子

2 つ`Platform::Guid`非等値のインスタンス。

### <a name="syntax"></a>構文

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>パラメーター

*guid1*<br/>
比較対象となる最初の `Platform::Guid`。

*guid2*<br/>
比較対象となる 2 番目の `Platform::Guid`。

### <a name="return-value"></a>戻り値

True の場合、2 つ`Platform::Guid`インスタンスが等しくないです。

## <a name="operator-less"></a> Guid::operator&lt;演算子

2 つ`Platform::Guid`順序付けのインスタンス。

### <a name="syntax"></a>構文

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>パラメーター

*guid1*<br/>
比較対象となる最初の `Platform::Guid`。

*guid2*<br/>
比較対象となる 2 番目の `Platform::Guid`。

### <a name="return-value"></a>戻り値

True の場合*guid1*前に順序付けは*guid2*します。 各に扱える後辞書式、順序付けは`Platform::Guid`4 つの 32 ビット符号なしの値の配列である場合にします。 これにより、SQL Server または、.NET Framework によって使用される順序付けされていないもは文字列形式を辞書式順序と同じ。

この演算子が提供されているように`Guid`オブジェクトは、C++ 標準ライブラリでより簡単に使用できます。

## <a name="operator-call"></a> Guid::operator() 演算子

暗黙的に変換を`Platform::Guid`を[GUID 構造体](https://msdn.microsoft.com/library/windows/desktop/aa373931)します。

### <a name="syntax"></a>構文

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>戻り値

A [GUID 構造体](https://msdn.microsoft.com/library/windows/desktop/aa373931)します。

## <a name="see-also"></a>関連項目

[Platform 名前空間](../cppcx/platform-namespace-c-cx.md)
