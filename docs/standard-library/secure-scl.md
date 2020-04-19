---
title: _SECURE_SCL
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
ms.openlocfilehash: 1af084363fc0d6d1723a9af7b633779f92ed2b38
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450539"
---
# <a name="securescl"></a>_SECURE_SCL

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) に置き換えられています。このマクロは、[チェックを行う反復子](../standard-library/checked-iterators.md)を有効にするかどうかを定義します。 既定では、チェックを行う反復子はデバッグ ビルドで有効になっており、製品版ビルドで無効になっています。

> [!IMPORTANT]
> _SECURE_SCL マクロの直接使用は非推奨とされます。 代わりに、チェックを行う反復子の設定を制御するには、[レベル] を使用します。 詳細については、「[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)」を参照してください。

## <a name="remarks"></a>Remarks

チェックを行う反復子が有効になっている場合、反復子の安全でない使用によってランタイム エラーが発生し、プログラムが終了します。 チェックを行う反復子を有効にするには、[レベル] を1または2に設定します。 これは、_SECURE_SCL 設定1または enabled に相当します。

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

チェックを行う反復子を無効にするには、[レベル] を0に設定します。 これは、0または disabled の _SECURE_SCL 設定に相当します。

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

チェックを行う反復子に関する警告を無効にする方法の詳細については、「[_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)」を参照してください。

## <a name="see-also"></a>関連項目

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[チェックを行う反復子](../standard-library/checked-iterators.md)\
[反復子のデバッグのサポート](../standard-library/debug-iterator-support.md)\
[安全なライブラリ: C++ 標準ライブラリ](../standard-library/safe-libraries-cpp-standard-library.md)
