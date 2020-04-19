---
title: const_mem_fun_t クラス
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_t
helpviewer_keywords:
- const_mem_fun_t class
ms.assetid: f169d381-019b-4a0e-a9a3-54da6d948270
ms.openlocfilehash: 5263612a26b2bcb606ad712a2a8e0a521ce9437a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688202"
---
# <a name="const_mem_fun_t-class"></a>const_mem_fun_t クラス

参照引数による初期化を行うときに、引数を使用しない const メンバー関数を単項関数オブジェクトとして呼び出せるようにするアダプター クラス。 C++ 11 では非推奨となりました。 C++ 17 では削除されています。

## <a name="syntax"></a>構文

```cpp
template <class Result, class Type>
class const_mem_fun_t : public unary_function <Type *, Result>
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type* Pleft) const;
};
```

### <a name="parameters"></a>パラメーター

*Pm* \
関数オブジェクトに変換されるクラス `Type` のメンバー関数へのポインター。

*Pleft* \
*Pm*メンバー関数が呼び出されるオブジェクト。

## <a name="return-value"></a>戻り値

適合可能な単項関数。

## <a name="remarks"></a>Remarks

クラステンプレートは、プライベートメンバーオブジェクト内の `Type` クラスのメンバー関数へのポインターである必要がある、 *Pm*のコピーを格納します。 これは、(`Pleft` -> \* `Pm`) () **const**を返すように `operator()` メンバー関数を定義します。

## <a name="example"></a>例

`const_mem_fun_t` のコンストラクターは通常は直接使用されません。ヘルパー関数 `mem_fun` を使用してメンバー関数を適合させます。 メンバー関数アダプターの使用例については、「[mem_fun](../standard-library/functional-functions.md#mem_fun)」を参照してください。
