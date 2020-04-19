---
title: mem_fun1_t クラス
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_t
helpviewer_keywords:
- mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
ms.openlocfilehash: 00d9322a8f0530da2e48b3f16fb52c00f9d1b075
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687735"
---
# <a name="mem_fun1_t-class"></a>mem_fun1_t クラス

ポインター引数で初期化するときに、1つの引数を使用する `non_const` メンバー関数を二項関数オブジェクトとして呼び出すことができるようにするアダプタークラス。 C++ 11 では非推奨となりました。 C++ 17 では削除されています。

## <a name="syntax"></a>構文

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_t : public binary_function<Type *, Arg, Result> {
    explicit mem_fun1_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type* _Pleft,
    Arg right) const;
};
```

### <a name="parameters"></a>パラメーター

*Pm \ (_r)*
関数オブジェクトに変換されるクラス `Type` のメンバー関数へのポインター。

*_Pleft* \
*Pm*メンバー関数が呼び出されるオブジェクト。

*右*\
*Pm*に渡される引数。

## <a name="return-value"></a>戻り値

適合可能な二項関数。

## <a name="remarks"></a>Remarks

クラステンプレートには、プライベートメンバーオブジェクト内の `Type` クラスのメンバー関数へのポインターである必要がある、 *Pm*のコピーが格納されます。 このメソッドは、( **_Pleft** -> \* `_Pm`) (**right**) を返すように、メンバー関数 `operator()` を定義します。

## <a name="example"></a>例

`mem_fun1_t` のコンストラクターは通常は直接使用されません。ヘルパー関数 `mem_fun` を使用してメンバー関数を適合させます。 メンバー関数アダプターの使用例については、「[mem_fun](../standard-library/functional-functions.md#mem_fun)」を参照してください。
