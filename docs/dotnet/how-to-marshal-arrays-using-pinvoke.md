---
title: '方法: 配列をマーシャ リングを使用して PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling [C++], arrays
- platform invoke [C++], arrays
- interop [C++], arrays
- data marshaling [C++], arrays
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
ms.openlocfilehash: 60b49135928e3dadffc2a3c7a422646d2f3a768d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325443"
---
# <a name="how-to-marshal-arrays-using-pinvoke"></a>方法: 配列をマーシャ リングを使用して PInvoke

このトピックでは、C スタイルの文字列は、CLR の文字列型を使用して呼び出すことができますを受け入れるどのネイティブ関数を説明します<xref:System.String>.NET Framework プラットフォーム呼び出しのサポートを使用します。 P/invoke は、ほとんどのコンパイル時エラーを報告するには、タイプ セーフでないし、実装に時間がかかることができますを提供するため、visual C++ プログラマが (可能な) 場合、代わりに、C++ Interop 機能を使用することが推奨されます。 P/invoke は、唯一のオプションでアンマネージ API が DLL としてパッケージ化し、ソース コードが使用できない場合 (それ以外の場合を参照してください[を使用して C++ Interop (暗黙の PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md))。

## <a name="example"></a>例

ネイティブおよびマネージ配列にはメモリに異なる方法でレイアウト、ためには、変換、またはマーシャ リングが必要がありますマネージ/アンマネージ境界上で正常に転送します。 このトピックでは、マネージ コードから単純な (blitable) 項目の配列をネイティブ関数に渡す方法を示します。

一般に、データのマネージ/アンマネージのマーシャ リングの場合は true、<xref:System.Runtime.InteropServices.DllImportAttribute>属性が使用される各ネイティブ関数のマネージ エントリ ポイントを作成するために使用します。 引数としての配列を受け取る関数の場合、<xref:System.Runtime.InteropServices.MarshalAsAttribute>属性は、データをマーシャ リングする方法をコンパイラに指定するにも使用する必要があります。 次の例では、<xref:System.Runtime.InteropServices.UnmanagedType>を C スタイル配列として、マネージ配列をマーシャ リングするかを示す列挙を使用します。

次のコードは、アンマネージとマネージ モジュールで構成されます。 非管理対象のモジュールは、整数の配列を受け取る関数を定義する DLL です。 2 番目のモジュールは、この関数インポートしますが、マネージ配列の観点から定義を使用して管理対象のコマンド ライン アプリケーション、<xref:System.Runtime.InteropServices.MarshalAsAttribute>配列が呼び出されたときに、ネイティブの配列に変換されることを指定する属性。

マネージ モジュールは、/clr でコンパイルされます。

```cpp
// TraditionalDll4.cpp
// compile with: /LD /EHsc
#include <iostream>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAnArray(int len, int[]);
}

void TakesAnArray(int len, int a[]) {
   printf_s("[unmanaged]\n");
   for (int i=0; i<len; i++)
      printf("%d = %d\n", i, a[i]);
}
```

```cpp
// MarshalBlitArray.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL {
   [DllImport("TraditionalDLL4.dll")]
   static public void TakesAnArray(
   int len,[MarshalAs(UnmanagedType::LPArray)]array<int>^);
};

int main() {
   array<int>^ b = gcnew array<int>(3);
   b[0] = 11;
   b[1] = 33;
   b[2] = 55;
   TraditionalDLL::TakesAnArray(3, b);

   Console::WriteLine("[managed]");
   for (int i=0; i<3; i++)
      Console::WriteLine("{0} = {1}", i, b[i]);
}
```

従来のマネージ コードに、DLL の部分は公開されていませんことに注意してください。 #include ディレクティブ。 実際には、DLL は実行時にのみアクセスをするための機能に関する問題はと共にインポートされる<xref:System.Runtime.InteropServices.DllImportAttribute>コンパイル時に検出されません。

## <a name="see-also"></a>関連項目

[C++ での明示的な PInvoke (DllImport 属性) の使用方法](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
