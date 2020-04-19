---
title: mem_fun_t クラス
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_t
helpviewer_keywords:
- mem_fun_t class
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
ms.openlocfilehash: 3c6606fe4d2df3b6068c3bb8194dc380344f7d97
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689378"
---
# <a name="mem_fun_t-class"></a>mem_fun_t クラス

ポインター引数を使用して初期化するときに、引数を取らない `non_const` メンバー関数を単項関数オブジェクトとして呼び出すことができるようにするアダプタークラス。 C++ 11 では非推奨となりました。 C++ 17 では削除されています。

## <a name="syntax"></a>構文

```cpp
template <class Result, class Type>
class mem_fun_t : public unary_function<Type *, Result> {
    explicit mem_fun_t(Result (Type::* _Pm)());

    Result operator()(Type* _Pleft) const;
};
```

### <a name="parameters"></a>パラメーター

*Pm \ (_r)*
関数オブジェクトに変換されるクラス `Type` のメンバー関数へのポインター。

*_Pleft* \
*Pm*メンバー関数が呼び出されるオブジェクト。

## <a name="return-value"></a>戻り値

適合可能な単項関数。

## <a name="remarks"></a>Remarks

クラステンプレートには、プライベートメンバーオブジェクト内の `Type` クラスのメンバー関数へのポインターである必要がある、 *Pm*のコピーが格納されます。 このメソッドは、(`_Pleft` ->*  `_Pm`) () を返すように、メンバー関数 `operator()` を定義します。

## <a name="example"></a>例

`mem_fun_t` のコンストラクターは通常は直接使用されません。ヘルパー関数 `mem_fun` を使用してメンバー関数を適合させます。 メンバー関数アダプターの使用例については、「[mem_fun](../standard-library/functional-functions.md#mem_fun)」を参照してください。
