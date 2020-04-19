---
title: 純粋なコードと検証可能なコード (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], verifiable assemblies
- /clr compiler option [C++], mixed assemblies
- pure MSIL [C++]
- verifiable assemblies [C++]
- verifiably type-safe code [C++]
- /clr compiler option [C++], pure assemblies
- .NET Framework [C++], pure and verifiable code
- assemblies [C++], mixed code
- verifiable assemblies [C++], about verifiable assemblies
- mixed assemblies [C++], about mixed assemblies
- pure MSIL [C++], about pure code
- assemblies [C++], verifiable code
- mixed assemblies [C++]
- assemblies [C++], pure code
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
ms.openlocfilehash: 66f3b5a33791d20297cde6e6223ba65189a99682
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384715"
---
# <a name="pure-and-verifiable-code-ccli"></a>検証可能な純粋なコード (C +/cli CLI)

.NET プログラミングに対して、Visual Studio 2017 の Visual C を使用して混在アセンブリの作成をサポート、 [/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)コンパイラ オプション。 **/Clr: 純粋な**と **/clr:safe**オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。 コードが安全なまたは、検証可能なをする必要がある場合に移植することをお勧めします。C#します。

## <a name="mixed-clr"></a>混合 (/clr)

混在アセンブリ (コンパイルした **/clr**)、アンマネージ両方を含めるし、.NET の機能を使用するようにできるので、管理対象のパーツには、ネイティブ コードも含めることができます。 このため、プロジェクト全体を書き直すことなく、.NET 機能を使用するようにアプリケーションやコンポーネントを更新できます。 Visual C を使用して、この方法でマネージ コードとネイティブ コードを混在させると、C++ Interop は呼び出されます。 詳細については、次を参照してください。[混在 (ネイティブおよびマネージ) アセンブリ](../dotnet/mixed-native-and-managed-assemblies.md)と[ネイティブと .NET の相互運用性](../dotnet/native-and-dotnet-interoperability.md)します。

マネージ アセンブリから P/invoke を通じてネイティブ Dll への呼び出しでは、コンパイルされますが、セキュリティ設定によっては実行時に失敗する可能性があります。

コンパイラは渡されますが確認不可能なアセンブリとなる 1 つのコーディング例があります。スコープ解決演算子を使用し、オブジェクト インスタンスを通じて仮想関数を呼び出す場合です。  たとえば、`MyObj -> A::VirtualFunction();` のように指定します。

## <a name="see-also"></a>関連項目

- [C++/CLI (Visual C++) による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
