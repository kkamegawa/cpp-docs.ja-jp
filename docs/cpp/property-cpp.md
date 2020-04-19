---
title: property (C++)
ms.date: 11/04/2016
f1_keywords:
- property_cpp
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
ms.openlocfilehash: ece1016b7a18873dfa477b0f8b6ae4271a0f8001
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301488"
---
# <a name="property-c"></a>property (C++)

**Microsoft 固有の仕様**

この属性は、クラスまたは構造体の定義の非静的 "仮想データ メンバー" に適用できます。 コンパイラは、参照を関数呼び出しに変更することにより、これらの "仮想データ メンバー" をデータ メンバーとして処理します。

## <a name="syntax"></a>構文

```
   __declspec( property( get=get_func_name ) ) declarator
   __declspec( property( put=put_func_name ) ) declarator
   __declspec( property( get=get_func_name, put=put_func_name ) ) declarator
```

## <a name="remarks"></a>Remarks

コンパイラがメンバー選択演算子の右側で、この属性で宣言されたデータ メンバーを表示する場合 ("**.**「または」**->**") に変換する操作、`get`または`put`関数は、このような式は、左辺値または右辺値かどうかによって異なります。 さらに複雑なコンテキストなど"`+=`"、両方の手順を実行して、再書き込みが実行される`get`と`put`します。

この属性は、クラスまたは構造体の定義の空の配列の宣言でも使用できます。 例えば:

```cpp
__declspec(property(get=GetX, put=PutX)) int x[];
```

前のステートメントは、`x[]` を 1 つ以上の配列インデックスで使用できることを示します。 この例では、`i=p->x[a][b]` は `i=p->GetX(a, b)` になります。また、`p->x[a][b] = i` は `p->PutX(a, b, i);` になります。

**Microsoft 固有の仕様はここまで**

## <a name="example"></a>例

```cpp
// declspec_property.cpp
struct S {
   int i;
   void putprop(int j) {
      i = j;
   }

   int getprop() {
      return i;
   }

   __declspec(property(get = getprop, put = putprop)) int the_prop;
};

int main() {
   S s;
   s.the_prop = 5;
   return s.the_prop;
}
```

## <a name="see-also"></a>関連項目

[__declspec](../cpp/declspec.md)<br/>
[キーワード](../cpp/keywords-cpp.md)