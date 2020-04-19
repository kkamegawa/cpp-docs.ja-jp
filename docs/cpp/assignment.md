---
title: 代入
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
ms.openlocfilehash: 1e6d715011cfaab7e250e23a9a31bb3f0c83f36a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184340"
---
# <a name="assignment"></a>代入

代入演算子 (**=**) は、厳密に言えば、二項演算子。 この宣言は他の二項演算子と同じですが、次の例外があります。

- 非静的メンバー関数である必要があります。 いいえ**演算子 =** 非メンバー関数として宣言することができます。
- 派生クラスにより継承されません。
- 既定の**演算子 =** が存在しない場合は、クラス型の場合、コンパイラによって関数を生成できます。

次の例では、代入演算子を宣言する方法を示しています。

```cpp
class Point
{
public:
    int _x, _y;

    // Right side of copy assignment is the argument.
    Point& operator=(const Point&);
};

// Define copy assignment operator.
Point& Point::operator=(const Point& otherPoint)
{
    _x = otherPoint._x;
    _y = otherPoint._y;

    // Assignment operator returns left side of assignment.
    return *this;
}

int main()
{
    Point pt1, pt2;
    pt1 = pt2;
}
```

指定された引数が、式の右側にあります。 演算子は、代入の完了後に左側の値を返す代入演算子の動作を保持するオブジェクトを返します。 など、割り当ての組み合わせが可能です。

```cpp
pt1 = pt2 = pt3;
```

コピー代入演算子では、コピー コンス トラクターと混同しないようにします。 後者と呼ばれる新しいオブジェクトの構築時に、既存のものから。

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> 従うことをお勧め、 [3 つのルール](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming))コピー代入演算子を定義するクラスでは、コピー コンス トラクターを明示的にも定義する必要があります、こと、デストラクターと、c++ 11 以降に移動コンス トラクターと移動代入演算子。

## <a name="see-also"></a>関連項目

- [演算子のオーバーロード](../cpp/operator-overloading.md)
- [コピー コンストラクターとコピー代入演算子 (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)