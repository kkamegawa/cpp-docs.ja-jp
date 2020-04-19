---
title: ユーザー定義の演算子 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined operators under /clr
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
ms.openlocfilehash: cf80eb4c440c1308e8ea06a563c18569e4e4ddf2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384505"
---
# <a name="user-defined-operators-ccli"></a>ユーザー定義の演算子 (C++/CLI)

マネージ型の場合、ユーザー定義の演算子は、静的メンバーまたはインスタンス メンバー、またはグローバル スコープで許可されます。 ただし、Visual C 以外の言語で記述されているクライアントにメタデータを介してアクセスできるは静的演算子のみです。

参照型でこれらのいずれかに静的なユーザー定義演算子のパラメーターのいずれかの必要があります。

- ハンドル (`type` ^)、外側の型のインスタンスにします。

- 参照型の間接参照 (`type`^ (& a) または型 ^ %)それを囲む型のインスタンスへのハンドル。

値の型でこれらのいずれかに静的なユーザー定義演算子のパラメーターのいずれかの必要があります。

- 外側の値の型と同じ型。

- ポインター型の間接参照 (`type`^)、外側の型にします。

- 参照型の間接参照 (`type`% または`type`&)、外側の型にします。

- 参照型の間接参照 (`type`^ % または`type`^ (& a)) のハンドルにします。

次の演算子を定義できます。

|演算子|単項/バイナリ形式ですか。|
|--------------|--------------------------|
|!|単項|
|!=|2 項|
|%|2 項|
|&|単項演算子および 2 項演算子|
|&&|2 項|
|*|単項演算子および 2 項演算子|
|+|単項演算子および 2 項演算子|
|++|単項|
|,|2 項|
|-|単項演算子および 2 項演算子|
|--|単項|
|->|単項|
|/|2 項|
|<|2 項|
|<<|2 項|
|\<=|2 項|
|=|2 項|
|==|2 項|
|>|2 項|
|>=|2 項|
|>>|2 項|
|^|2 項|
|False|単項|
|true|単項|
|&#124;|2 項|
|&#124;&#124;|2 項|
|~|単項|

## <a name="example"></a>例

```cpp
// mcppv2_user-defined_operators.cpp
// compile with: /clr
using namespace System;
public ref struct X {
   X(int i) : m_i(i) {}
   X() {}

   int m_i;

   // static, binary, user-defined operator
   static X ^ operator + (X^ me, int i) {
      return (gcnew X(me -> m_i + i));
   }

   // instance, binary, user-defined operator
   X^ operator -( int i ) {
      return gcnew X(this->m_i - i);
   }

   // instance, unary, user-defined pre-increment operator
   X^ operator ++() {
      return gcnew X(this->m_i++);
   }

   // instance, unary, user-defined post-increment operator
   X^ operator ++(int i) {
      return gcnew X(this->m_i++);
   }

   // static, unary user-defined pre- and post-increment operator
   static X^ operator-- (X^ me) {
      return (gcnew X(me -> m_i - 1));
   }
};

int main() {
   X ^hX = gcnew X(-5);
   System::Console::WriteLine(hX -> m_i);

   hX = hX + 1;
   System::Console::WriteLine(hX -> m_i);

   hX = hX - (-1);
   System::Console::WriteLine(hX -> m_i);

   ++hX;
   System::Console::WriteLine(hX -> m_i);

   hX++;
   System::Console::WriteLine(hX -> m_i);

   hX--;
   System::Console::WriteLine(hX -> m_i);

   --hX;
   System::Console::WriteLine(hX -> m_i);
}
```

```Output
-5
-4
-3
-2
-1
-2
-3
```

## <a name="example"></a>例

次の例は、使用する場合にのみ使用される演算子合成 **/clr**をコンパイルします。 複合演算子の使用は二項演算子の割り当てフォームを作成します、1 つの場合は定義されず、CLR 型の代入演算子の左側にあるが。

```cpp
// mcppv2_user-defined_operators_2.cpp
// compile with: /clr
ref struct A {
   A(int n) : m_n(n) {};
   static A^ operator + (A^ r1, A^ r2) {
      return gcnew A( r1->m_n + r2->m_n);
   };
   int m_n;
};

int main() {
   A^ a1 = gcnew A(10);
   A^ a2 = gcnew A(20);

   a1 += a2;   // a1 = a1 + a2   += not defined in source
   System::Console::WriteLine(a1->m_n);
}
```

```Output
30
```

## <a name="see-also"></a>関連項目

[クラスと構造体](../extensions/classes-and-structs-cpp-component-extensions.md)
