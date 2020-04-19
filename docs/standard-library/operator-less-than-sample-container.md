---
title: operator&lt; (&lt;sample container&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::operator<
- operator<
- std.<
- <
- std.operator<
- std::<
helpviewer_keywords:
- < operator, comparing specific objects
- operator<, valarrays
- < operator
- operator <, valarrays
ms.assetid: 31027dd6-53be-428b-b950-1dcb25393597
ms.openlocfilehash: fc2a14d882b5ccfbfdaae543c76ca673f9018a59
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687334"
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt; (&lt;sample container&gt;)

> [!NOTE]
> このトピックは、 C++ C++標準ライブラリで使用されているコンテナーの非機能例として、Microsoft ドキュメントに記載されています。 詳細については、「[C++ Standard Library Containers (C++ 標準ライブラリ コンテナ―)](../standard-library/stl-containers.md)」をご覧ください。

Overloads**演算子 <** クラステンプレート[コンテナー](../standard-library/sample-container-class.md)の2つのオブジェクトを比較します。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
bool operator<(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>戻り値

`lexicographical_compare(left.begin, left.end, right.begin, right.end)`を返します。

## <a name="see-also"></a>関連項目

[\<sample container>](../standard-library/sample-container.md)\
[開始](../standard-library/container-class-begin.md)\
[end](../standard-library/container-class-end.md)