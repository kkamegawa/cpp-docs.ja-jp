---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: 58ebd91fb4fa32cf31d2c49429d0445b92fe0c82
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449905"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

C 標準ライブラリヘッダー \<の > をインクルードし、関連`std`する名前を名前空間に追加します。 このヘッダーをインクルードすると、C 標準ライブラリヘッダーの外部リンケージを使用して宣言され`std`た名前が、名前空間で宣言されます。

> [!NOTE]
> \<assert > ではマクロが定義`static_assert`されていません。

## <a name="syntax"></a>構文

```cpp
#include <cassert>
```

## <a name="macros"></a>[マクロ]

```cpp
#define assert(E)
```

### <a name="remarks"></a>Remarks

`assert(E)`は定数です。が最後に定義また`assert`は再定義された場所で NDEBUG が定義されている場合、またはブール型*に変換さ*れた場合は**true**に評価されます。

## <a name="see-also"></a>関連項目

[assert マクロ、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)\
[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリの概要](../standard-library/cpp-standard-library-overview.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
