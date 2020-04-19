---
title: コンパイラの警告 (レベル 1) C4930
ms.date: 11/04/2016
f1_keywords:
- C4930
helpviewer_keywords:
- C4930
ms.assetid: 89a206c9-c536-4186-8e81-1cde3e7f4f5b
ms.openlocfilehash: b21cc6364692eb2f3b1d56b03d175df1f2ad7ee8
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050280"
---
# <a name="compiler-warning-level-1-c4930"></a>コンパイラの警告 (レベル 1) C4930

' prototype ': プロトタイプ関数は呼び出されません (変数の定義が意図されていました)

コンパイラは、未使用の関数プロトタイプを検出しました。 プロトタイプが変数宣言として意図されている場合は、開始かっこと終了かっこを削除します。

次の例では、C4930 が生成されます。

```cpp
// C4930.cpp
// compile with: /W1
class Lock {
public:
   int i;
};

void f() {
   Lock theLock();   // C4930
   // try the following line instead
   // Lock theLock;
}

int main() {
}
```

C4930 は、コンパイラが関数プロトタイプ宣言と関数呼び出しを区別できない場合にも発生する可能性があります。

次の例では、C4930 が生成されます。

```cpp
// C4930b.cpp
// compile with: /EHsc /W1

class BooleanException
{
   bool _result;

public:
   BooleanException(bool result)
      : _result(result)
   {
   }

   bool GetResult() const
   {
      return _result;
   }
};

template<class T = BooleanException>
class IfFailedThrow
{
public:
   IfFailedThrow(bool result)
   {
      if (!result)
      {
         throw T(result);
      }
   }
};

class MyClass
{
public:
   bool MyFunc()
   {
      try
      {
         IfFailedThrow<>(MyMethod()); // C4930

         // try one of the following lines instead
         // IfFailedThrow<> ift(MyMethod());
         // IfFailedThrow<>(this->MyMethod());
         // IfFailedThrow<>((*this).MyMethod());

         return true;
      }
      catch (BooleanException e)
      {
         return e.GetResult();
      }
   }

private:
   bool MyMethod()
   {
      return true;
   }
};

int main()
{
   MyClass myClass;
   myClass.MyFunc();
}
```

上のサンプルでは、引数を受け取らないメソッドの結果は、名前のないローカルクラス変数のコンストラクターに引数として渡されます。 この呼び出しを明確にするには、ローカル変数に名前を付けます。または、メソッド呼び出しの前に、適切な pointer-to-member 演算子と共にオブジェクトインスタンスを指定します。