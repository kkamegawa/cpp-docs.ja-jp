---
title: コンパイラ エラー C2259
ms.date: 11/04/2016
f1_keywords:
- C2259
helpviewer_keywords:
- C2259
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
ms.openlocfilehash: 403d674eae696eb42a837aef9d6e97c4b5b8f6c2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758789"
---
# <a name="compiler-error-c2259"></a>コンパイラ エラー C2259

'クラス' : 抽象クラスをインスタンス化できません。

抽象クラスまたは抽象構造体のインスタンスが宣言されています。

1 つ以上の純粋仮想関数を持つクラスまたは構造体をインスタンス化することはできません。 派生クラスのオブジェクトをインスタンス化するには、派生クラスが各純粋仮想関数をオーバーライドする必要があります。

詳細については、「[暗黙的な抽象クラス](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes)」を参照してください。

次の例では、C2259 が生成されます。

```cpp
// C2259.cpp
// compile with: /c
class V {
public:
   void virtual func() = 0;
};
class A : public V {};
class B : public V {
public:
   void func();
};
V v;  // C2259, V is an abstract class
A a;  // C2259, A inherits func() as pure virtual
B b;  // OK, B defines func()
```

インターフェイスから派生して、パブリック以外のアクセス許可を持つインターフェイス メソッドを派生クラスに実装する場合は、常に C2259 が発生する可能性があります。  これは、コンパイラでは、派生クラスに実装されたインターフェイス メソッドはパブリック アクセスを持つことが想定されているために発生します。 より制限の厳しいアクセス許可を持つインターフェイスのメンバー関数を実装する場合、コンパイラはそれらをインターフェイスに定義されるインターフェイス メソッドの実装とは見なさず、代わりにその派生クラスを抽象クラスとします。

この問題を回避する方法は 2 つあります。

- 実装されるメソッドのアクセス許可をパブリックにします。

- 派生クラスに実装されるインターフェイス メソッドに対してスコープ解決演算子を使用して、実装されるメソッド名をインターフェイスの名前で修飾します。

C2259 は、Visual Studio 2005 で実行された準拠作業の結果としても発生する可能性があります。 **/zc: wchar_t**は既定でオンになっています。 このような場合は、 **/zc: wchar_t**を指定してコンパイルすることによって解決できます。以前のバージョンの動作を取得するには、型を更新して互換性があるかどうかを確認します。 「[/Zc:wchar_t (wchar_t をネイティブ型として認識)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)」を参照してください。

次の例では、C2259 が生成されます。

```cpp
// C2259b.cpp
// compile with: /c
#include <windows.h>

class MyClass {
public:
   // WCHAR now typedef'ed to wchar_t
   virtual void func(WCHAR*) = 0;
};

class MyClass2 : MyClass {
public:
   void func(unsigned short*);
};

MyClass2 x;   // C2259

// OK
class MyClass3 {
public:
   virtual void func(WCHAR*) = 0;
   virtual void func2(wchar_t*) = 0;
   virtual void func3(unsigned short*) = 0;
};

class MyClass4 : MyClass3 {
public:
   void func(WCHAR*) {}
   void func2(wchar_t*) {}
   void func3(unsigned short*) {}
};

MyClass4 y;
```

次の例では、C2259 が生成されます。

```cpp
// C2259c.cpp
// compile with: /clr
interface class MyInterface {
   void MyMethod();
};

ref class MyDerivedClass: public MyInterface {
private:
   // Uncomment the following line to resolve.
   // public:
   void MyMethod(){}
   // or the following line
   // void MyInterface::MyMethod() {};
};

int main() {
   MyDerivedClass^ instance = gcnew MyDerivedClass; // C2259
}
```
