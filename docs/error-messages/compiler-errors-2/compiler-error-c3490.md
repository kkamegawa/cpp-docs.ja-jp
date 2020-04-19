---
title: コンパイラ エラー C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: 940eae39222548ec74bda8ccb38e669748ffa74f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738402"
---
# <a name="compiler-error-c3490"></a>コンパイラ エラー C3490

'var' は const オブジェクトを通じてアクセスされているため変更できません

`const` メソッドで宣言されているラムダ式は、変更不能なメンバー データを変更することはできません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- メソッド宣言から `const` 修飾子を削除します。

## <a name="example"></a>使用例

次の例では、 `_i` メソッドでメンバー変数 `const` を変更するため、C3490 が生成されます。

```cpp
// C3490a.cpp
// compile with: /c

class C
{
   void f() const
   {
      auto x = [=]() { _i = 20; }; // C3490
   }

   int _i;
};
```

## <a name="example"></a>使用例

次の例では、メソッド宣言から `const` 修飾子を削除して C3490 を解決します。

```cpp
// C3490b.cpp
// compile with: /c

class C
{
   void f()
   {
      auto x = [=]() { _i = 20; };
   }

   int _i;
};
```

## <a name="see-also"></a>参照

[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)
