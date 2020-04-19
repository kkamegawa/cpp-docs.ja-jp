---
title: 混在 (ネイティブおよびマネージド) アセンブリ
ms.date: 09/18/2018
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
ms.openlocfilehash: 043390a2ebefcadac300b7fb0b05ae7f5ed411f3
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447288"
---
# <a name="mixed-native-and-managed-assemblies"></a>混在 (ネイティブおよびマネージ) アセンブリ

混在アセンブリは、アンマネージ マシン語命令と MSIL 命令の両方を含むことができます。 これにより、それらを呼び出し、ネイティブの C++ ライブラリとの互換性を維持しながら、.NET コンポーネントによって呼び出されることができます。 混在アセンブリを使用して、開発者は .NET とネイティブ C++ コードの組み合わせを使用してアプリケーションを作成できます。

1 つのモジュールを再コンパイルしてネイティブ C++ コード全体で構成される既存のライブラリを .NET プラットフォームに移動するなど、 **/clr**コンパイラ スイッチ。 以降、このモジュールで .NET 機能を使用できるようになりますが、アプリケーションの残りの部分との互換性は維持されたままです。 同じファイル内の関数ごとに、マネージ コードとネイティブ コンパイルの間を決定することも (を参照してください[マネージ、アンマネージ](../preprocessor/managed-unmanaged.md))。

Visual C を使用してマネージの混在のアセンブリの生成をサポートするのみ、 **/clr**コンパイラ オプション。 **/Clr: 純粋な**と **/clr:safe**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。 純粋なまたは検証可能なマネージ アセンブリが必要な場合は、c# を使用して作成することをお勧めします。

以前のバージョンの MicrosoftC++コンパイラ ツールセットには、次の 3 つの種類のマネージ アセンブリの生成がサポートされています。 混合、純粋、および検証可能な。 後者の 2 つは、後ほど[純粋で検証可能なコード (C +/cli CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)します。

## <a name="in-this-section"></a>このセクションの内容

[方法: /Clr:pure に移行します。](../dotnet/how-to-migrate-to-clr.md)<br/>
アプリケーションへの .NET 機能の導入またはアプリケーション内の .NET 機能の更新を行うための推奨処理手順について説明します。

[方法: MFC および ATL コードを使用して、/clr をコンパイルします。](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
共通言語ランタイムをターゲットに既存の MFC および ATL プログラムをコンパイルする方法について説明します。

[混在アセンブリの初期化](../dotnet/initialization-of-mixed-assemblies.md)<br/>
"ローダー ロック" の問題とそのソリューションについて説明します。

[混在アセンブリのためのライブラリ サポート](../dotnet/library-support-for-mixed-assemblies.md)<br/>
ネイティブ ライブラリを使用する方法について説明します **/clr**コンパイルします。

[パフォーマンスに関する考慮事項](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
混在アセンブリとデータ マーシャリングのパフォーマンスへの影響について説明します。

[アプリケーション ドメインと Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
アプリケーション ドメインに対する Visual C++ サポートについて説明します。

[ダブル サンキング](../dotnet/double-thunking-cpp.md)<br/>
マネージド関数のネイティブ エントリ ポイントのパフォーマンスへの影響について説明します。

[/Clr で CLR シャット ダウン時に消費して構築された COM オブジェクトの例外の回避](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
コンパイルされた COM オブジェクトを使用するマネージ アプリケーションの適切なシャット ダウンする方法について説明します **/clr**します。

[方法: CRT ライブラリ DLL との依存関係を削除して部分信頼アプリケーションを作成する](../dotnet/create-a-partially-trusted-application.md)<br/>
Msvcm90.dll との依存関係を削除することで、Visual C を使用して部分的に信頼された共通言語ランタイム アプリケーションを作成する方法について説明します。

混在アセンブリのコーディングのガイドラインの詳細については、MSDN の記事を参照してください。 [、概要のマネージ/アンマネージ コードの相互運用性](https://msdn.microsoft.com/library/ms973872.aspx)します。

## <a name="see-also"></a>関連項目

- [ネイティブと .NET の相互運用性](../dotnet/native-and-dotnet-interoperability.md)
