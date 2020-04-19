---
title: コンパイラの警告 (レベル 1) C4436
ms.date: 11/04/2016
f1_keywords:
- C4436
helpviewer_keywords:
- C4436
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
ms.openlocfilehash: 762a458072a0a1104cd1af55ef1f61772485b6c9
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810610"
---
# <a name="compiler-warning-level-1-c4436"></a>コンパイラの警告 (レベル 1) C4436

コンストラクターまたはデストラクター内の仮想ベース ' class1 ' から ' class2 ' への dynamic_cast は、/vd2 を使用して部分的に構築されたオブジェクトで失敗するか、#pragma vtordisp (2) が有効な ' class2 ' を定義しています。

コンパイラで、次の特性を持つ `dynamic_cast` 操作が検出されました。

- キャストは、基底クラスポインターから派生クラスポインターへのキャストです。

- 派生クラスは、実質的に基底クラスを継承します。

- 派生クラスには、仮想ベースの `vtordisp` フィールドがありません。

- キャストは、派生クラスのコンストラクターまたはデストラクター、または派生クラスからさらに継承するクラスにあります。

警告は、部分的に構築されたオブジェクトで動作している場合に、`dynamic_cast` が正しく実行されない可能性があることを示します。  これは、派生コンストラクターまたはデストラクターが、さらに派生したオブジェクトのサブオブジェクト上で動作している場合に発生します。  警告で指定された派生クラスがそれ以上派生していない場合は、警告を無視できます。

## <a name="example"></a>使用例

次の例では、C4436 を生成し、不足している `vtordisp` フィールドから発生するコード生成の問題を示します。

```cpp
// C4436.cpp
// To see the warning and runtime assert, compile with: /W1
// To eliminate the warning and assert, compile with: /W1 /vd2
//       or compile with: /W1 /DFIX
#include <cassert>

struct A
{
public:
    virtual ~A() {}
};

#if defined(FIX)
#pragma vtordisp(push, 2)
#endif
struct B : virtual A
{
    B()
    {
        A* a = static_cast<A*>(this);
        B* b = dynamic_cast<B*>(a);     // C4436
        assert(this == b);              // assert unless compiled with /vd2
    }
};
#if defined(FIX)
#pragma vtordisp(pop)
#endif

struct C : B
{
    int i;
};

int main()
{
    C c;
}
```

## <a name="see-also"></a>参照

[dynamic_cast 演算子](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[コンパイラの警告 (レベル 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)