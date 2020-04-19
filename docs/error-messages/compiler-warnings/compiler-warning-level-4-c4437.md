---
title: コンパイラの警告 (レベル 4) C4437
ms.date: 11/04/2016
f1_keywords:
- C4437
helpviewer_keywords:
- C4437
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
ms.openlocfilehash: 6cd50d5c4d79b82c135ab4e84ec390dee9e906ef
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810655"
---
# <a name="compiler-warning-level-4-c4437"></a>コンパイラの警告 (レベル 4) C4437

/vd2 を使用してコンパイルする一部のコンテキストでは、仮想ベース ' class1 ' から ' class2 ' への dynamic_cast が失敗し、#pragma vtordisp (2) が有効になっている ' class2 ' が定義される可能性があります

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

コンパイラで、次の特性を持つ `dynamic_cast` 操作が検出されました。

- キャストは、基底クラスポインターから派生クラスポインターへのキャストです。

- 派生クラスは、実質的に基底クラスを継承します。

- 派生クラスには、仮想ベースの `vtordisp` フィールドがありません。

- キャストが、派生クラスのコンストラクターまたはデストラクターで見つからないか、派生クラスからさらに継承されるクラス (それ以外の場合はコンパイラ警告 C4436 が発行されます) にあります。

警告は、部分的に構築されたオブジェクトで動作している場合に、`dynamic_cast` が正しく実行されない可能性があることを示します。  この状況は、外側の関数が、警告で指定された派生クラスを継承するクラスのコンストラクターまたはデストラクターから呼び出された場合に発生します。  警告で指定された派生クラスがそれ以上派生しない場合、またはオブジェクトの構築時または破棄時に外側の関数が呼び出されない場合は、警告を無視できます。

## <a name="example"></a>使用例

次の例では、C4437 を生成し、不足している `vtordisp` フィールドから発生するコード生成の問題を示します。

```cpp
// C4437.cpp
// To see the warning and runtime assert, compile with: /W4
// To eliminate the warning and assert, compile with: /W4 /vd2
//       or compile with: /W4 /DFIX
#pragma warning(default : 4437)
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
        func();
    }

    void func()
    {
        A* a = static_cast<A*>(this);
        B* b = dynamic_cast<B*>(a);     // C4437
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
[コンパイラの警告 (レベル 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)