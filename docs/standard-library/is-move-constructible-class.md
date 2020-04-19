---
title: is_move_constructible クラス
ms.date: 10/24/2019
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 9585a932a34a24769201aaa379525a9b4c181e41
ms.sourcegitcommit: 33a898bf976c65f998b4e88a84765a0cef4193a8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920089"
---
# <a name="is_move_constructible-class"></a>is_move_constructible クラス

移動操作を使用して型を構築できるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>パラメーター

*T* \
評価される型。

## <a name="remarks"></a>Remarks

移動操作を使用して型*T*を構築できる場合は**true**に評価される型述語。 この述語は `is_constructible<T, T&&>` と同じです。 移動コンストラクターを持たないが、`const T&` 引数を受け取るコピーコンストラクターを持つ型*T*は、`std::is_move_constructible`を満たします。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
