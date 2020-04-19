---
title: pointer_to_binary_function クラス
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_binary
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
ms.openlocfilehash: 890ebb7d4c2b8fbd51a4460e21efba3e763ead7e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687187"
---
# <a name="pointer_to_binary_function-class"></a>pointer_to_binary_function クラス

二項関数ポインターを適応性のある二項関数に変換します。 C++ 11 では非推奨となりました。 C++ 17 では削除されています。

## <a name="syntax"></a>構文

```cpp
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```

### <a name="parameters"></a>パラメーター

*pfunc* \
変換する二項関数。

*左*\
*\*pfunc* が呼び出される左辺のオブジェクト。

*右*\
*\*pfunc* が呼び出される右側のオブジェクト。

## <a name="return-value"></a>戻り値

クラステンプレートには、`pfunc` のコピーが格納されます。 @No__t_1 を返すように、メンバー関数 `operator()` を定義します。

## <a name="remarks"></a>Remarks

二項関数ポインターは関数オブジェクトであり、パラメーターとして二項関数を想定する C++ 標準ライブラリの任意のアルゴリズムに渡される場合がありますが、適応性はありません。 これをアダプターで使用するには (値をバインドする、negator で使用するなど)、入れ子にされた型 `first_argument_type`、`second_argument_type`、およびそのような適合を可能にする `result_type` を指定する必要があります。 `pointer_to_binary_function` による変換によって、関数アダプターを二項関数ポインターと共に使用できるようになります。

## <a name="example"></a>例

`pointer_to_binary_function` のコンストラクターが直接使用されることはほとんどありません。 `pointer_to_binary_function` アダプターの述語を宣言および使用する方法の例については、ヘルパー関数 [ptr_fun](../standard-library/functional-functions.md#ptr_fun) をご覧ください。
