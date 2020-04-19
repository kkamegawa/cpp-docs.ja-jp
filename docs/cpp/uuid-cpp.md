---
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: c121ad99dfbe0021a263f324ccdb9a95441bba33
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740460"
---
# <a name="uuid-c"></a>uuid (C++)

**Microsoft 固有の仕様**

コンパイラは、 **uuid**属性を使用して、宣言または定義された (完全な COM オブジェクト定義のみ) クラスまたは構造体に GUID をアタッチします。

## <a name="syntax"></a>構文

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>Remarks

**Uuid**属性は、引数として文字列を受け取ります。 この文字列は、 **{}** 区切り記号の有無に関係なく、通常のレジストリ形式で GUID に名前を付けます。 例えば:

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

この属性は、再宣言で適用できます。 これにより、システムヘッダーはなどのインターフェイスの定義、 `IUnknown`および他のヘッダー ( \<comdef .h > など) の再宣言によって GUID を指定できます。

[__Uuidof](../cpp/uuidof-operator.md)キーワードを適用して、ユーザー定義型にアタッチされている定数 GUID を取得できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__declspec](../cpp/declspec.md)<br/>
[キーワード](../cpp/keywords-cpp.md)