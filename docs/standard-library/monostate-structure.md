---
title: monostate 構造体
ms.date: 04/04/2019
f1_keywords:
- variant/std::monostate
helpviewer_keywords:
- monostate struct
ms.openlocfilehash: f083b5f4abd6e9fc482007744683342f7ab92fc0
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269334"
---
# <a name="monostate-struct"></a>monostate 構造体

クラス monostate はバリアント型の既定値を構築できることに一種の代替の型として機能します。

## <a name="syntax"></a>構文

```cpp
struct monostate;

constexpr bool operator<(monostate, monostate) noexcept;
constexpr bool operator>(monostate, monostate) noexcept;
constexpr bool operator<=(monostate, monostate) noexcept;
constexpr bool operator>=(monostate, monostate) noexcept;
constexpr bool operator==(monostate, monostate) noexcept;
constexpr bool operator!=(monostate, monostate) noexcept;
```
