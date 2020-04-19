---
title: slice_array クラス
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: 358348a57b823fcea82cd296967c83778819361d
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688958"
---
# <a name="slice_array-class"></a>slice_array クラス

Valarray のスライスによって定義されたサブセット配列間の演算を提供することによってスライスオブジェクトをサポートする、内部の補助クラステンプレート。

## <a name="syntax"></a>構文

```cpp
template <class Type>
class slice_array : public slice {
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

このクラスは、**valarray\<Type>** オブジェクトから選択する要素のシーケンスを説明するクラス [slice](../standard-library/slice-class.md) のオブジェクトとともに、クラス [valarray](../standard-library/valarray-class.md) **\<Type>** のオブジェクトへの参照を格納するオブジェクトを表します。

クラステンプレートは、特定の valarray 操作によって間接的に作成され、プログラムで直接使用することはできません。 スライスの添字演算子によって使用される、内部の補助クラステンプレート。

`slice_array`\< **Type**> `valarray`< **Type**:: `operator[]` ( `slice`)

@No__t_0 オブジェクトを構築するには、valarray `va` のスライス[`sl`&#91;に&#93;va sl](../standard-library/valarray-class.md#op_at)形式の式を記述する必要があります。 クラス slice_array のメンバー関数は、`valarray<Type>` に対して定義されている対応する関数シグネチャのように動作します。ただし、選択された要素のシーケンスのみが影響を受けます。 slice_array によって制御されるシーケンスは、スライスのコンストラクターの 3 つのパラメーター (スライス内の最初の要素のインデックス、要素の数、要素間の距離) によって定義されます。 **Va**によって宣言された valarray `va` からの slice_array 切り取り [`slice` (2, 5, 3)] は `va` からインデックス2、5、8、11、14の要素を選択します。 プロシージャが有効であるためには、これらのインデックスが有効である必要があります。

## <a name="example"></a>例

slice_array の宣言方法や使用方法の例については、[slice::slice](../standard-library/slice-class.md#slice) の例を参照してください。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<valarray>

**名前空間:** std

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
