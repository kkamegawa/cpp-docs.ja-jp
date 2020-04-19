---
title: '方法: 文字列をマーシャ リングを使用して PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
ms.openlocfilehash: f316e33f1711ea0053fb68c0af7e89f90b793e05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404404"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>方法: 文字列をマーシャ リングを使用して PInvoke

このトピックの C スタイルの文字列は、CLR の文字列を使用して呼び出すことができますを受け入れる関数をネイティブ .NET Framework プラットフォーム呼び出しのサポートを使用して system::string を入力します。 P/invoke は、ほとんどのコンパイル時エラーを報告するには、タイプ セーフでないし、実装に時間がかかることができますを提供するため、visual C++ プログラマが (可能な) 場合、代わりに、C++ Interop 機能を使用することが推奨されます。 アンマネージ API が DLL としてパッケージ化し、ソース コードが使用できない場合、P/invoke は唯一のオプションが、それ以外の場合を参照してください[を使用して C++ Interop (暗黙の PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)します。

マネージ コードとアンマネージの文字列にはメモリに異なる方法でレイアウト、アンマネージ関数に管理対象から文字列を渡すのでが必要です、<xref:System.Runtime.InteropServices.MarshalAsAttribute>文字列データをマーシャ リングするために必要な変換メカニズムを挿入するようコンパイラに指示する属性正しくかつ安全にします。

組み込みのデータ型のみを使用する関数と同様<xref:System.Runtime.InteropServices.DllImportAttribute>、ネイティブ関数には - C スタイルの文字列を識別するハンドルを受け取るようにこれらのエントリ ポイントを定義する代わりに - 文字列を渡すために、マネージ エントリ ポイントを宣言するために使用、<xref:System.String>型代わりに使用できます。 これには、コンパイラが必要な変換を実行するコードを挿入するように求められます。 各関数の引数でアンマネージ関数には、文字列を受け取り、<xref:System.Runtime.InteropServices.MarshalAsAttribute>を C スタイル文字列としてネイティブ関数に文字列オブジェクトをマーシャ リングすることを示す属性を使用する必要があります。

## <a name="example"></a>例

次のコードは、アンマネージ コードとマネージ モジュールで構成されます。 非管理対象のモジュールは、char * の形式での C スタイルの ANSI 文字列を受け取る TakesAString という名前の関数を定義する DLL です。 マネージ モジュールは、TakesAString 関数をインポートしますが、取得、char の代わりにマネージ System.String としてそれを定義するコマンド ライン アプリケーション\*します。 <xref:System.Runtime.InteropServices.MarshalAsAttribute>属性を使用して、どのマネージ文字列をマーシャ リング TakesAString が呼び出されたときに指定します。

```
// TraditionalDll2.cpp
// compile with: /LD /EHsc
#include <windows.h>
#include <stdio.h>
#include <iostream>

using namespace std;

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAString(char*);
}

void TakesAString(char* p) {
   printf_s("[unmanaged] %s\n", p);
}
```

```
// MarshalString.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL
{
   [DllImport("TraditionalDLL2.dll")]
      static public void
      TakesAString([MarshalAs(UnmanagedType::LPStr)]String^);
};

int main() {
   String^ s = gcnew String("sample string");
    Console::WriteLine("[managed] passing managed string to unmanaged function...");
   TraditionalDLL::TakesAString(s);
   Console::WriteLine("[managed] {0}", s);
}
```

この手法では、文字列のマネージ コピーで、ネイティブ関数によって、文字列に加えられた変更は反映されませんので、アンマネージ ヒープ上に構築する文字列のコピーをによりします。

従来のマネージ コードに、DLL の部分は公開されていませんことに注意してください。 #include ディレクティブ。 実際には、DLL にはアクセス時にのみの機能に問題が取り込まれるように`DllImport`コンパイル時に検出されません。

## <a name="see-also"></a>関連項目

[C++ での明示的な PInvoke (DllImport 属性) の使用方法](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
