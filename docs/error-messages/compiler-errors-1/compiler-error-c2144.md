---
title: コンパイラ エラー C2144
ms.date: 11/04/2016
f1_keywords:
- C2144
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
ms.openlocfilehash: a75330d26b0924e60f7e46d10d617341709d7e23
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353496"
---
# <a name="compiler-error-c2144"></a>コンパイラ エラー C2144

> 構文エラー: '*型*'によって先行されなければなりません'*トークン*'

予想コンパイラ*トークン*と*型*代わりにします。

このエラーは、右中かっこ、右かっこ、またはセミコロンで発生する可能性があります。

C2144 は、空白文字を含む CLR キーワードからマクロを作成しようとしているときにも発生します。

型の転送を実行しようとしている場合にも、C2144 を表示があります。 参照してください[Type Forwarding (C +/cli CLI)](../../extensions/type-forwarding-cpp-cli.md)詳細についてはします。

## <a name="examples"></a>使用例

次の例では、C2144 を生成し、その修正方法を示しています。

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

次の例では、C2144 を生成し、その修正方法を示しています。

```cpp
// C2144_2.cpp
// compile with: /clr /c
ref struct X {

   property double MultiDimProp[,,] {   // C2144
   // try the following line instead
   // property double MultiDimProp[int , int, int] {
      double get(int, int, int) { return 1; }
      void set(int i, int j, int k, double l) {}
   }

   property double MultiDimProp2[] {   // C2144
   // try the following line instead
   // property double MultiDimProp2[int] {
      double get(int) { return 1; }
      void set(int i, double l) {}
   }
};
```