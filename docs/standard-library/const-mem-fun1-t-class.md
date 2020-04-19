---
title: const_mem_fun1_t クラス
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: 1af44635400037c6359b13c4f2925c3ac7f2d9d5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689752"
---
# <a name="const_mem_fun1_t-class"></a>const_mem_fun1_t クラス

ポインター引数による初期化を行うときに、1 つの引数を使用する **const** メンバー関数を二項関数オブジェクトとして呼び出せるようにするアダプター クラス。 C++ 11 では非推奨となりました。 C++ 17 では削除されています。

## <a name="syntax"></a>構文

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_t : public binary_function<const Type *, Arg, Result>
{
    explicit const_mem_fun1_t(Result (Type::* member_ptr)(Arg) const);
    Result operator()(const Type* left, Arg right) const;
};
```

### <a name="parameters"></a>パラメーター

*member_ptr* \
関数オブジェクトに変換されるクラス `Type` のメンバー関数へのポインター。

*左*\
*Member_ptr*メンバー関数が呼び出される**const**オブジェクト。

*右*\
*Member_ptr*に渡される引数。

## <a name="return-value"></a>戻り値

適合可能な二項関数。

## <a name="remarks"></a>Remarks

クラステンプレートには、 *member_ptr*のコピーが格納されます。これは、プライベートメンバーオブジェクト内の `Type` クラスのメンバー関数へのポインターである必要があります。 @No__t_1 を返すように、メンバー関数 `operator()` を定義します。

## <a name="example"></a>例

`const_mem_fun1_t` のコンストラクターが直接使用されることはほとんどありません。 メンバー関数を調整するには、`mem_fn` を使用します。 メンバー関数アダプターの使用例については、「 [mem_fn](../standard-library/functional-functions.md#mem_fn) 」を参照してください。
