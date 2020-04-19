---
title: _HAS_ITERATOR_DEBUGGING
ms.date: 11/04/2016
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
ms.openlocfilehash: a1e3017ed7c6def18ce02d99dc8253b69c11ab58
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448832"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) に置き換えられたこのマクロは、デバッグ ビルドで反復子のデバッグ機能を有効にするかどうかを定義します。 既定では、反復子のデバッグはデバッグ ビルドで有効になっており、製品版ビルドで無効になっています。 詳細については、「[反復子のデバッグのサポート](../standard-library/debug-iterator-support.md)」を参照してください。

> [!IMPORTANT]
> デバッグマクロを直接使用することは非推奨とされます。 (_s) 代わりに、反復子デバッグ設定を制御するには、[レベル] を使用します。 詳細については、「[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)」を参照してください。

## <a name="remarks"></a>Remarks

デバッグビルドで反復子デバッグを有効にするには、[レベル] を2に設定します。 これは、"1" または "enabled" のデバッグ設定に相当します。

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

Retail ビルドでは、レベルを2に設定する (およびデバッグを1に設定することはできません)。 (_s)

デバッグビルドでデバッグ反復子を無効にするには、[レベル] を0または1に設定します。 これは、0または disabled のデバッグ設定と同じになります (_s):

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>関連項目

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[反復子のデバッグのサポート](../standard-library/debug-iterator-support.md)\
[チェックを行う反復子](../standard-library/checked-iterators.md)\
[安全なライブラリ: C++ 標準ライブラリ](../standard-library/safe-libraries-cpp-standard-library.md)
