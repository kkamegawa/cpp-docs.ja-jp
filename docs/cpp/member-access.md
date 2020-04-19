---
title: メンバー アクセス
ms.date: 11/04/2016
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
ms.openlocfilehash: 34527f818b135fd5af629ebb69feaffd03b715fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301631"
---
# <a name="member-access"></a>メンバー アクセス

メンバー アクセス演算子をオーバー ロードによって、クラス メンバーへのアクセスを制御できます (**->**)。 この演算子は、この使用方法では単項演算子と見なされ、オーバーロードされる演算子関数は、クラス メンバー関数である必要があります。 したがって、このような関数の宣言は次のとおりです。

## <a name="syntax"></a>構文

```
class-type *operator->()
```

## <a name="remarks"></a>Remarks

場所*クラス型*このオペレーターが所属するクラスの名前を指定します。 メンバー アクセス演算子関数は、非静的メンバー関数である必要があります。

この演算子は、逆参照やカウントの使用の前にポインターを検証する "スマート ポインター" を実装するために使用されます (多くの場合はポインターの逆参照演算子と共に)。

**.** メンバー アクセス演算子をオーバー ロードすることはできません。

## <a name="see-also"></a>関連項目

[演算子のオーバーロード](../cpp/operator-overloading.md)