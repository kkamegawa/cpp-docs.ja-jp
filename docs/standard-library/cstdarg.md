---
title: '&lt;cstdarg&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdarg>
helpviewer_keywords:
- cstdarg header
ms.assetid: 639b4ef7-8408-4640-9343-41631f0ab663
ms.openlocfilehash: 0b45d5f591c5394ffa861e75169dce70f53b1baf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448026"
---
# <a name="ltcstdarggt"></a>&lt;cstdarg&gt;

C 標準ライブラリヘッダー \<stdarg.h > をインクルードし、関連`std`する名前を名前空間に追加します。 このヘッダーをインクルードすると、C 標準ライブラリヘッダーの外部リンケージを使用して宣言され`std`た名前が、名前空間で宣言されます。

## <a name="syntax"></a>構文

```cpp
#include <cstdarg>
```

## <a name="namespace-and-macros"></a>名前空間とマクロ

```cpp
namespace std {
    using va_list = see below;
}

#define va_arg(V, P)
#define va_copy(VDST, VSRC)
#define va_end(V)
#define va_start(V, P)
```

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリの概要](../standard-library/cpp-standard-library-overview.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
