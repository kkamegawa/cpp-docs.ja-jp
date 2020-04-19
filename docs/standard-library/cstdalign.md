---
title: '&lt;cstdalign が&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdalign>
- cstdalign
- __alignas_is_defined
- __alignof_is_defined
helpviewer_keywords:
- cstdalign header
- __alignas_is_defined
- __alignof_is_defined
ms.assetid: 9d570924-d299-4225-9a58-8c4c820f5903
ms.openlocfilehash: 603a590190c50495aa80f1b41a574149eb8f760a
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2019
ms.locfileid: "68342841"
---
# <a name="ltcstdaligngt"></a>&lt;cstdalign が&gt;

一部C++の標準ライブラリの実装では、このヘッダーには C \<標準ライブラリヘッダー stdalign > が含まれており、 `std`関連する名前が名前空間に追加されます。 このヘッダーは MSVC に実装されて\<いないため、cstdalign が > `__alignas_is_defined`ヘッダー `__alignof_is_defined`は互換性マクロおよびを定義します。

> [!NOTE]
> > Stdalign ヘッダーでは、のキーワードでC++あるマクロが定義されているため、これを含めても効果はありません。 \< Stdalign \<> ヘッダーは、でC++は非推奨とされます。 \<Cstdalign が > ヘッダーは c++ 17 では非推奨とされており、draft c++ 20 standard では削除されています。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<cstdalign が >

**名前空間:** std

## <a name="macros"></a>[マクロ]

| マクロ | 説明 |
| - | - |
| `__alignas_is_defined` | 整数定数1に展開する C 互換マクロ。 |
| `__alignof_is_defined` | 整数定数1に展開する C 互換マクロ。 |

## <a name="see-also"></a>関連項目

[ヘッダーファイルのリファレンス](cpp-standard-library-header-files.md)\
[C++標準ライブラリの概要](cpp-standard-library-overview.md)\
[C++標準ライブラリのスレッドセーフ](thread-safety-in-the-cpp-standard-library.md)
