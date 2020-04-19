---
title: char_traits&lt;wchar_t&gt; 構造体
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: a2f8a882020ddb3d87436d08b3d85ea9407b1c08
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458977"
---
# <a name="chartraitsltwchartgt-struct"></a>char_traits&lt;wchar_t&gt; 構造体

テンプレート構造体**char_traits\<chartype**を特殊化したクラスを**wchar_t**型の要素に > します。

## <a name="syntax"></a>構文

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>Remarks

特殊化により、構造体は、この種類の**wchar_t**のオブジェクトを操作するライブラリ関数を利用できます。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<string>

**名前空間:** std

## <a name="see-also"></a>関連項目

[char_traits 構造体](../standard-library/char-traits-struct.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
