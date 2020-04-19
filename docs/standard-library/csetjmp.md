---
title: '&lt;csetjmp&gt;'
ms.date: 11/04/2016
f1_keywords:
- <csetjmp>
helpviewer_keywords:
- csetjmp header
ms.assetid: 8f21fddd-5e9b-4219-a848-581cdd3569d9
ms.openlocfilehash: 8f3a1a622776d5dd2ef3d22aaa3436933c5a7137
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452397"
---
# <a name="ltcsetjmpgt"></a>&lt;csetjmp&gt;

標準 C ライブラリ ヘッダー \<setjmp.h> をインクルードし、関連する名前を `std` 名前空間に追加します。

## <a name="syntax"></a>構文

```cpp
#include <csetjmp>

using jmp_buf = see below;
```

## <a name="functions"></a>関数

```cpp
[[noreturn]] void longjmp(jmp_buf env, int val);
```

## <a name="macros"></a>[マクロ]

```cpp
#define setjmp(env)
```

## <a name="remarks"></a>Remarks

このヘッダーをインクルードすると、標準 C ライブラリ ヘッダーの外部リンケージで宣言された名前が、`std` 名前空間でも宣言されます。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリの概要](../standard-library/cpp-standard-library-overview.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
