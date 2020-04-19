---
title: nullopt_t 構造体
ms.date: 08/04/2019
f1_keywords:
- optional/std::nullopt_t
- optional/std::nullopt
ms.openlocfilehash: 1f453a5d75de3f6dedb133d55c094a4f4274e08f
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957046"
---
# <a name="nullopt_t-struct"></a>nullopt_t 構造体

型`nullopt_t`は、[オプション](optional-class.md)のオブジェクトに値が含まれていないことを示すために使用される一意の空の型です。

型`nullopt` `optional`の定数は、型が初期化されていない状態であることを示します。 `nullopt_t` `optional`オブジェクトを初期化するか、またはオブジェクトと比較するために使用できます。

## <a name="syntax"></a>構文

```cpp
struct nullopt_t;
inline constexpr nullopt_t nullopt{ /*implementation-defined*/ };
```

## <a name="see-also"></a>関連項目

[\<オプション >](optional.md)\
[省略可能なクラス](optional-class.md)
