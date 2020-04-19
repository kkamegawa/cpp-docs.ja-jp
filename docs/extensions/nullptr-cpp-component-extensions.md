---
title: nullptr (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: 05aaaa8a0d0056e0f5318f5e9329d90824760728
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515637"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr (C++/CLI および C++/CX)

**nullptr** キーワードは、"*Null ポインター値*" を表します。 Null ポインター値は、オブジェクト ハンドル、内部ポインター、またはネイティブ ポインターの型がオブジェクトを指していないことを示すために使用します。

**nullptr** はマネージド コードまたはネイティブ コードのいずれかに使用します。 コンパイラからは、マネージドおよびネイティブの Null ポインター値に適した異なる命令が発行されます。 このキーワードの ISO 標準の C++ バージョンの使用については、「[nullptr](../cpp/nullptr.md)」を参照してください。

**__nullptr** キーワードは Microsoft 固有であり、**nullptr** と同じ意味ですが、ネイティブ コードにのみ適用されます。 ネイティブの C/C++ コードで **nullptr** を使用してから [/clr](../build/reference/clr-common-language-runtime-compilation.md) コンパイラ オプションを指定してコンパイルすると、コンパイラでは、**nullptr** が示す Null ポインター値がネイティブかマネージドかを判断できません。 コンパイラに意図を明確に伝えるには、マネージド値を指定する場合は **nullptr**、ネイティブ値を指定する場合は **__nullptr** を使用します。

**nullptr** キーワードは、Visual Basic では **Nothing**、C# では **null** と同じです。

## <a name="usage"></a>使用法

**nullptr** キーワードは、ハンドル、ネイティブ ポインター、または関数の引数を使用できる場所であれば、どこでも使用できます。

**nullptr** キーワードは型ではないので、以下には使用できません。

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr` (ただし `throw (Object^)nullptr;` は機能します)

**nullptr** キーワードは、以下のポインター型の初期化に使用できます。

- ネイティブ ポインター

- Windows ランタイム ハンドル

- マネージド ハンドル

- マネージド内部ポインター

**nullptr** キーワードを使用すると、参照が使用される前にポインターまたはハンドルの参照が null かどうかをテストできます。

エラー チェックに Null ポインター値を使用する言語間の関数呼び出しは、正しく解釈されます。

ハンドルを 0 に初期化することはできません。**nullptr** のみを使用できます。 オブジェクト ハンドルに定数 0 を割り当てると、ボックス化された `Int32` と `Object^` へのキャストが生成されます。

## <a name="example"></a>例

次のコード例に、ハンドル、ネイティブ ポインター、または関数の引数を使用できる場所であれば、**nullptr** キーワードをどこでも使用できることを示します。 また、この例では、参照の使用前にチェックするために **nullptr** キーワードを使用しています。

```cpp
// mcpp_nullptr.cpp
// compile with: /clr
value class V {};
ref class G {};
void f(System::Object ^) {}

int main() {
// Native pointer.
   int *pN = nullptr;
// Managed handle.
   G ^pG = nullptr;
   V ^pV1 = nullptr;
// Managed interior pointer.
   interior_ptr<V> pV2 = nullptr;
// Reference checking before using a pointer.
   if (pN == nullptr) {}
   if (pG == nullptr) {}
   if (pV1 == nullptr) {}
   if (pV2 == nullptr) {}
// nullptr can be used as a function argument.
   f(nullptr);   // calls f(System::Object ^)
}
```

## <a name="example"></a>例

次のコード例に、ネイティブ ポインターに **nullptr** と 0 を同様に使用できることを示します。

```cpp
// mcpp_nullptr_1.cpp
// compile with: /clr
class MyClass {
public:
   int i;
};

int main() {
   MyClass * pMyClass = nullptr;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");

   pMyClass = 0;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");
}
```

```Output
pMyClass == nullptr

pMyClass == 0

pMyClass == nullptr

pMyClass == 0
```

## <a name="example"></a>例

次のコード例に、**nullptr** が任意の型へのハンドル、または任意の型へのネイティブ ポインターと解釈されることを示します。 異なる型へのハンドルを使用した関数のオーバーロードの場合、あいまいさのエラーが発生します。 **nullptr** では明示的に型にキャストする必要があります。

```cpp
// mcpp_nullptr_2.cpp
// compile with: /clr /LD
void f(int *){}
void f(int ^){}

void f_null() {
   f(nullptr);   // C2668
   // try one of the following lines instead
   f((int *) nullptr);
   f((int ^) nullptr);
}
```

## <a name="example"></a>例

次のコード例に、**nullptr** のキャストが許可され、**nullptr** 値を含むキャスト型へのポインターまたはハンドルが返されることを示します。

```cpp
// mcpp_nullptr_3.cpp
// compile with: /clr /LD
using namespace System;
template <typename T>
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type

int main() {
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)

   // Delete the following line to resolve.
   f(nullptr);

   f(0);   // T = int, call f(int)
}
```

## <a name="example"></a>例

次のコード例に、**nullptr** を関数パラメーターとして使用できることを示します。

```cpp
// mcpp_nullptr_4.cpp
// compile with: /clr
using namespace System;
void f(Object ^ x) {
   Console::WriteLine("test");
}

int main() {
   f(nullptr);
}
```

```Output
test
```

## <a name="example"></a>例

次のコード例に、ハンドルが宣言され、明示的に初期化されていない場合、既定で **nullptr** に初期化されることを示します。

```cpp
// mcpp_nullptr_5.cpp
// compile with: /clr
using namespace System;
ref class MyClass {
public:
   void Test() {
      MyClass ^pMyClass;   // gc type
      if (pMyClass == nullptr)
         Console::WriteLine("NULL");
   }
};

int main() {
   MyClass ^ x = gcnew MyClass();
   x -> Test();
}
```

```Output
NULL
```

## <a name="example"></a>例

次のコード例に、`/clr` を使用してコンパイルするときに、**nullptr** をネイティブ ポインターに割り当てられることを示します。

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>要件

コンパイラ オプション:(必須ではありません。`/ZW` と `/clr` を含むすべてのコード生成オプションでサポートされています)

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)