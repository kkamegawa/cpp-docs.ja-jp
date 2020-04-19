---
title: '方法: 関数ポインターをマーシャ リングを使用して PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- interop [C++], callbacks and delegates
- platform invoke [C++], callbacks and delegates
- marshaling [C++], callbacks and delegates
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
ms.openlocfilehash: 031bda0f93d6a95aa3c774553aefca0647d0518c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400566"
---
# <a name="how-to-marshal-function-pointers-using-pinvoke"></a>方法: 関数ポインターをマーシャ リングを使用して PInvoke

このトピックでは、マネージ デリゲートを説明します。 .NET Framework P/invoke 機能を使用して関数をアンマネージとの相互運用時に、関数ポインターの代わりに使用できます。 ただし、Visual C プログラマは、P/invoke は、ほとんどのコンパイル時エラーを報告するには、タイプ セーフでないし、実装に時間がかかることができますを提供するため (可能な) 場合、代わりに、C++ Interop 機能を使用することが推奨されます。 アンマネージ API が DLL としてパッケージ化、ソース コードが使用できない場合は、P/invoke、唯一のオプションです。 それ以外の場合、次のトピックを参照してください。

- [C++ Interop (暗黙の PInvoke) の使用](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [方法: C++ Interop を使用してコールバックおよびデリゲートをマーシャリングする](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

引数は、ネイティブ関数ポインターの代わりにマネージ デリゲートを使用してマネージ コードから呼び出すことができます、関数ポインターを使用するアンマネージ Api。 コンパイラは自動的に関数ポインターとしてアンマネージ関数にデリゲートをマーシャ リングし、マネージ/アンマネージ移行のために必要なコードを挿入します。

## <a name="example"></a>例

次のコードは、アンマネージとマネージ モジュールで構成されます。 非管理対象のモジュールは、関数ポインターを受け取る TakesCallback という名前の関数を定義する DLL です。 このアドレスは、関数の実行に使用されます。

マネージ モジュールは、関数ポインターとネイティブ コードにマーシャ リングを使用してデリゲートを定義します。、<xref:System.Runtime.InteropServices.DllImportAttribute>マネージ コードにネイティブ TakesCallback 関数を公開する属性。 メインの関数で、デリゲートのインスタンスが作成され、TakesCallback 関数に渡されます。 プログラムの出力では、この関数がネイティブ TakesCallback 関数によって実行されることを示します。

管理対象の関数は、.NET Framework ガベージ コレクションをネイティブ関数の実行中に、デリゲートの再配置を阻止するマネージ デリゲートのガベージ コレクションを抑制します。

```cpp
// TraditionalDll5.cpp
// compile with: /LD /EHsc
#include <iostream>
#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   /* Declare an unmanaged function type that takes two int arguments
      Note the use of __stdcall for compatibility with managed code */
   typedef int (__stdcall *CALLBACK)(int);
   TRADITIONALDLL_API int TakesCallback(CALLBACK fp, int);
}

int TakesCallback(CALLBACK fp, int n) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n);
}
```

```cpp
// MarshalDelegate.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

public delegate int GetTheAnswerDelegate(int);
public value struct TraditionalDLL {
   [DllImport("TraditionalDLL5.dll")]
   static public int TakesCallback(GetTheAnswerDelegate^ pfn, int n);
};

int GetNumber(int n) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;
   return x + n;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   pin_ptr<GetTheAnswerDelegate^> pp = &fp;
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TraditionalDLL::TakesCallback(fp, 42);
}
```

従来を使用してマネージ コードに、DLL の部分は公開されていませんことに注意してください。 #include ディレクティブ。 実際には、DLL にはアクセス実行時にのみの機能に問題が取り込まれるように<xref:System.Runtime.InteropServices.DllImportAttribute>コンパイル時に検出されません。

## <a name="see-also"></a>関連項目

[C++ での明示的な PInvoke (DllImport 属性) の使用方法](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
