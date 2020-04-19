---
title: const_mem_fun1_ref_t クラス
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: 76fae1ce29cb4c47870e45e8f946f6ff1fea1885
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688176"
---
# <a name="const_mem_fun1_ref_t-class"></a>const_mem_fun1_ref_t クラス

参照引数による初期化を行うときに、1 つの引数を使用する **const** メンバー関数を二項関数オブジェクトとして呼び出せるようにするアダプター クラス。 C++ 11 では非推奨となりました。 C++ 17 では削除されています。

## <a name="syntax"></a>構文

```cpp
template <class Result, class Type, class Arg>
    class const_mem_fun1_ref_t
        : public binary_function<Type, Arg, Result>
{
    explicit const_mem_fun1_ref_t(Result (Type::* Pm)(Arg) const);
    Result operator()(const Type& left, Arg right) const;
};
```

### <a name="parameters"></a>パラメーター

*Pm* \
関数オブジェクトに変換されるクラス `Type` のメンバー関数へのポインター。

*左*\
*Pm*メンバー関数が呼び出される**const**オブジェクト。

*右*\
*Pm*に渡される引数。

## <a name="return-value"></a>戻り値

適合可能な二項関数。

## <a name="remarks"></a>Remarks

クラステンプレートは、プライベートメンバーオブジェクト内の `Type` クラスのメンバー関数へのポインターである必要がある、 *Pm*のコピーを格納します。 これは、(\* `left` *Pm*) (`right`) **const**を返すように、そのメンバー関数 `operator()` を定義します。

## <a name="example"></a>例

`const_mem_fun1_ref_t` のコンストラクターは通常は直接使用されません。ヘルパー関数 `mem_fun_ref` を使用してメンバー関数を適合させます。 メンバー関数アダプターの使用例については、「[mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)」を参照してください。
