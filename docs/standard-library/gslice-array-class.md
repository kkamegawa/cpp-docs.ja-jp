---
title: gslice_array クラス
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice_array
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
ms.openlocfilehash: 68ce774128395e941ff80580a02c4ee28a74a4e4
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689594"
---
# <a name="gslice_array-class"></a>gslice_array クラス

Valarray の一般的なスライスによって定義されたサブセット配列間の演算を提供することによって一般的なスライスオブジェクトをサポートする、内部の補助クラステンプレート。

## <a name="syntax"></a>構文

```cpp
template <class Type>
class gslice_array : public gsplice {
public:
    typedef Type value_type;
    void operator=(const valarray<Type>& x) const;

    void operator=(const Type& x) const;

    void operator*=(const valarray<Type>& x) const;

    void operator/=(const valarray<Type>& x) const;

    void operator%=(const valarray<Type>& x) const;

    void operator+=(const valarray<Type>& x) const;

    void operator-=(const valarray<Type>& x) const;

    void operator^=(const valarray<Type>& x) const;

    void operator&=(const valarray<Type>& x) const;

    void operator|=(const valarray<Type>& x) const;

    void operator<<=(const valarray<Type>& x) const;

    void operator>>=(const valarray<Type>& x) const;

// The rest is private or implementation defined
}
```

## <a name="remarks"></a>Remarks

クラスは、クラス[valarray](../standard-library/valarray-class.md)  **\<Type >** の `va` オブジェクトへの参照、および `valarray<Type>` オブジェクトから選択する要素のシーケンスを記述するクラス[gslice](../standard-library/gslice-class.md)のオブジェクト `gs` を格納するオブジェクトを表します。

@No__t_0 オブジェクトを構築するには、 [va&#91;g&#93;](../standard-library/valarray-class.md#op_at)の形式の式を記述する必要があります。 クラス gslice_array のメンバー関数は、`valarray<Type>` に対して定義されている対応する関数シグネチャのように動作します。ただし、選択された要素のシーケンスのみが影響を受けます。

クラステンプレートは、特定の valarray 操作によって間接的に作成され、プログラムで直接使用することはできません。 代わりに、内部補助クラステンプレートがスライスの添字演算子によって使用されます。

`gslice_array`\< **Type**> `valarray`\< **Type**>:: `operator[]` ( **constgslice&** )

@No__t_0 オブジェクトを構築するには、valarray `va` のスライス `gsl` に `va[gsl]` フォームの式を記述する必要があります。 クラス gslice_array のメンバー関数は、`valarray<Type>` に対して定義されている対応する関数シグネチャのように動作します。ただし、選択された要素のシーケンスのみが影響を受けます。 gslice_array によって制御されるシーケンスは、スライスのコンストラクターの 3 つのパラメーター (最初のスライス内の最初の要素のインデックス、各スライス内の要素の数、各スライス内の要素間の距離) によって定義されます。

次に例を示します。

```cpp
const size_t lv[] = {2, 3};
const size_t dv[] = {7, 2};
const valarray<size_t> len(lv, 2), str(dv, 2);

// va[gslice(3, len, str)] selects elements with
//   indices 3, 5, 7, 10, 12, 14
```

プロシージャが有効であるためには、これらのインデックスが有効である必要があります。

## <a name="example"></a>例

slice_array の宣言方法や使用例については、[gslice::gslice](../standard-library/gslice-class.md#gslice) の例を参照してください。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<valarray>

**名前空間:** std

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
