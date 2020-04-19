---
title: '&lt;random&gt; 関数'
ms.date: 09/04/2019
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 3d94f607fc6b7bdf22d7f573f590b451dbaa718d
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273837"
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt; 関数

## <a name="generate_canonical"></a>generate_canonical

ランダム シーケンスから浮動小数点値を返します。

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>パラメーター

*RealType*\
浮動小数点整数型。 使用可能な型については、[\<random>](../standard-library/random.md) をご覧ください。

*列*\
使用するランダムなビット数。

*ジェネレーター*\
乱数ジェネレータークラス。

*世代*\
型*ジェネレーター*の乱数ジェネレーターのインスタンスへの参照。

### <a name="remarks"></a>Remarks

このテンプレート関数は`operator()` 、*ジェネレーション*のを繰り返し呼び出し、返された値を、指定`x`した数の仮数ビットがに`x`収集されるまで、 *realtype*型の浮動小数点値にパックします。 指定された数値は、(0 以外である必要がある)*ビット*の小さい方で、 *realtype*の仮数部のビット数が完全ではありません。 最初の呼び出しで最下位のビットが提供されます。 `x` が返されます。
