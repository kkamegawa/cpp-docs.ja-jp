---
title: '方法: 出力を指定するパラメーター'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 901257b92aaa5e13e6e79d612ca590b734e15881
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387221"
---
# <a name="how-to-specify-an-out-parameter"></a>方法: 出力を指定するパラメーター

このサンプルでは、関数のパラメーターを out パラメーターに指定する方法と、c# プログラムからその関数を呼び出す方法を示します。

Visual C で out パラメーターが指定された<xref:System.Runtime.InteropServices.OutAttribute>します。

## <a name="example"></a>例

このサンプルの最初の部分では、out パラメーターを持つ関数を含む型での Visual C DLL です。

```
// cpp_out_param.cpp
// compile with: /LD /clr:safe
using namespace System;
public value struct TestStruct {
   static void Test([Runtime::InteropServices::Out] String^ %s) {
      s = "a string";
   }
};
```

## <a name="example"></a>例

これは、前の例で作成した Visual C コンポーネントを使用する c# クライアントです。

```
// cpp_out_param_2.cs
// compile with: /reference:cpp_out_param.dll
using System;
class TestClass {
   public static void Main() {
      String t;
      TestStruct.Test(out t);
      System.Console.WriteLine(t);
   }
}
```

```Output
a string
```

## <a name="see-also"></a>関連項目

[C++ Interop (暗黙の PInvoke) の使用](../dotnet/using-cpp-interop-implicit-pinvoke.md)
