---
title: '方法: -Clr コンパイルでネイティブ型を使用します。'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
ms.openlocfilehash: 9979113ac4ffc062ddfe8654279af03036984f38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387202"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>方法: /Clr のコンパイルでネイティブ型を使用します。

ネイティブ型を定義することができます、 **/clr**コンパイルとどのように使用されるアセンブリ内からそのネイティブな型が無効です。 ただし、ネイティブ型は参照されているメタデータから使用できるようできません。

各アセンブリは、使用するすべてのネイティブ型の定義を含める必要があります。

詳細については、「[/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)」を参照してください。

## <a name="example"></a>例

このサンプルでは、定義して、ネイティブな型を使用するコンポーネントを作成します。

```
// use_native_type_in_clr.cpp
// compile with: /clr /LD
public struct NativeClass {
   static int Test() { return 98; }
};

public ref struct ManagedClass {
   static int i = NativeClass::Test();
   void Test() {
      System::Console::WriteLine(i);
   }
};
```

## <a name="example"></a>例

このサンプルでは、コンポーネントを使用するクライアントを定義します。 コンパイル単位で定義されている場合を除き、ネイティブな型を使用するとエラーはことに注意してください。

```
// use_native_type_in_clr_2.cpp
// compile with: /clr
#using "use_native_type_in_clr.dll"
// Uncomment the following 3 lines to resolve.
// public struct NativeClass {
//    static int Test() { return 98; }
// };

int main() {
   ManagedClass x;
   x.Test();

   System::Console::WriteLine(NativeClass::Test());   // C2653
}
```

## <a name="see-also"></a>関連項目

[C++ Interop (暗黙の PInvoke) の使用](../dotnet/using-cpp-interop-implicit-pinvoke.md)
