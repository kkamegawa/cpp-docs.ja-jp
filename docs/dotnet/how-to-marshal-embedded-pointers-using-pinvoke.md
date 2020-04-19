---
title: '方法: PInvoke を使用して埋め込みポインターをマーシャ リングします。'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- embedded pointers [C++]
- interop [C++], embedded pointers
- platform invoke [C++], embedded pointers
- marshaling [C++], embedded pointers
- data marshaling [C++], embedded pointers
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
ms.openlocfilehash: 943a1a2784a37353157cd38da7ebdc9827006fe5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325209"
---
# <a name="how-to-marshal-embedded-pointers-using-pinvoke"></a>方法: PInvoke を使用して埋め込みポインターをマーシャ リングします。

アンマネージ Dll に実装されている関数は、Platform Invoke (P/invoke) 機能を使用してマネージ コードから呼び出すことができます。 DLL のソース コードを使用できない場合の相互運用の唯一のオプションは、P/invoke します。 ただし、Visual C は、他の .NET 言語とは異なり、P/invoke の代替を提供します。 詳細については、次を参照してください。[を使用して C++ Interop (暗黙の PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)と[方法。埋め込み C++ Interop を使用して、ポインターをマーシャ リング](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)します。

## <a name="example"></a>例

ネイティブ コードに構造体の受け渡しには、データのレイアウトの観点からネイティブ構造体と等価のマネージ構造体を作成する必要があります。 ただし、ポインターを格納する構造体には、特別な処理が必要です。 構造体のマネージ バージョンのネイティブ構造体に埋め込まれた各ポインターのインスタンスを含める必要があります、<xref:System.IntPtr>型。 また、メモリのこれらのインスタンスは明示的に割り当てる必要がある初期化され、リリースを使用して、 <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A>、 <xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A>、および<xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>メソッド。

次のコードは、アンマネージとマネージ モジュールで構成されます。 非管理対象のモジュールは、ポインターを含む ListString と呼ばれる構造体を受け取る関数と TakesListStruct という名前の関数を定義する DLL です。 マネージ モジュールは TakesListStruct 関数をインポートし、する点を除いて、二重 * はで表されるネイティブ ListStruct に相当する MListStruct と呼ばれる構造体を定義するコマンド ライン アプリケーション、<xref:System.IntPtr>インスタンス。 TakesListStruct を呼び出す前に、メインの関数は、割り当て、このフィールドを参照するメモリを初期化します。

```cpp
// TraditionalDll6.cpp
// compile with: /EHsc /LD
#include <stdio.h>
#include <iostream>
#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct ListStruct {
   int count;
   double* item;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API void TakesListStruct(ListStruct);
}

void TakesListStruct(ListStruct list) {
   printf_s("[unmanaged] count = %d\n", list.count);
   for (int i=0; i<list.count; i++)
      printf_s("array[%d] = %f\n", i, list.item[i]);
}
```

```cpp
// EmbeddedPointerMarshalling.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MListStruct {
   int count;
   IntPtr item;
};

value struct TraditionalDLL {
    [DllImport("TraditionalDLL6.dll")]
   static public void TakesListStruct(MListStruct);
};

int main() {
   array<double>^ parray = gcnew array<double>(10);
   Console::WriteLine("[managed] count = {0}", parray->Length);

   Random^ r = gcnew Random();
   for (int i=0; i<parray->Length; i++) {
      parray[i] = r->NextDouble() * 100.0;
      Console::WriteLine("array[{0}] = {1}", i, parray[i]);
   }

   int size = Marshal::SizeOf(double::typeid);
   MListStruct list;
   list.count = parray->Length;
   list.item = Marshal::AllocCoTaskMem(size * parray->Length);

   for (int i=0; i<parray->Length; i++) {
      IntPtr t = IntPtr(list.item.ToInt32() + i * size);
      Marshal::StructureToPtr(parray[i], t, false);
   }

   TraditionalDLL::TakesListStruct( list );
   Marshal::FreeCoTaskMem(list.item);
}
```

従来を使用してマネージ コードに、DLL の部分は公開されていませんことに注意してください。 #include ディレクティブ。 実際には、DLL にはアクセス実行時にのみの機能に問題が取り込まれるように<xref:System.Runtime.InteropServices.DllImportAttribute>コンパイル時に検出されません。

## <a name="see-also"></a>関連項目

[C++ での明示的な PInvoke (DllImport 属性) の使用方法](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
