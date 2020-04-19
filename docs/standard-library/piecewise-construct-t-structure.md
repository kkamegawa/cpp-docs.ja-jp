---
title: piecewise_contruct_t 構造体
ms.date: 11/04/2016
f1_keywords:
- utility/std::piecewise_contruct_t
helpviewer_keywords:
- piecewise_contruct_t class
- piecewise_contruct_t structure
ms.openlocfilehash: 6a9a6af97ca5c7751d64cd1fa70c9d9eba87da7c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268364"
---
# <a name="piecewisecontructt-structure"></a>piecewise_contruct_t 構造体

構造体`piecewise_construct_t`は別のコンス トラクターと関数のオーバー ロードを維持するために使用する空の構造型です。 具体的には、`pair`でコンス トラクターを持つ`piecewise_construct_t`によって 2 つの後に、最初の引数として`tuple`引数。

## <a name="syntax"></a>構文

```cpp
struct piecewise_construct_t { explicit piecewise_construct_t() = default; };

inline constexpr piecewise_construct_t piecewise_construct{};
```
