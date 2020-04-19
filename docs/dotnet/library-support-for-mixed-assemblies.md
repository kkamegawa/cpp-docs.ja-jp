---
title: 混在アセンブリのためのライブラリ サポート
ms.date: 09/18/2018
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
ms.openlocfilehash: 42116c09d5b31cf669eb6d5d1e75eae60b2610a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312009"
---
# <a name="library-support-for-mixed-assemblies"></a>混在アセンブリのためのライブラリ サポート

Visual C、C++ 標準ライブラリ、C ランタイム ライブラリ (CRT) の使用をサポートする、ATL と MFC でコンパイルされたアプリケーションの[/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)します。 これにより、既存のアプリケーションも .NET Framework の機能を使用するためにこれらのライブラリを使用できます。

> [!IMPORTANT]
> **/Clr: 純粋な**と **/clr:safe**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

このサポートには、次の DLL とインポート ライブラリが含まれています。

- 使用してコンパイルする場合、Msvcmrt [d] .lib **/clr**します。 このインポート ライブラリへのリンクを混在アセンブリ。

このサポートは、関連するいくつかの利点を提供します。

- CRT と C++ 標準ライブラリは、混合コードを利用します。 CRT と C++ 標準ライブラリが提供されているは検証可能な; できません。最終的には、呼び出しはネイティブ コードから使用するため引き続き同じ CRT と C++ 標準ライブラリにルーティングされます。

- 混合イメージで統一された例外の処理を修正します。

- 混合イメージ内の C++ 変数の静的な初期化します。

- マネージ コードで、AppDomain ごとと、プロセスごとの変数をサポートします。

- 混在モード Dll を Visual Studio 2003 以前のバージョンでのコンパイルに適用されるローダー ロックに関する問題を解決します。

さらに、このサポートには、次の制限事項が表示されます。

- コンパイルされるコードに、CRT DLL モデルのみがサポートされている **/clr**します。 サポートする静的な CRT ライブラリがない **/clr**をビルドします。

## <a name="see-also"></a>関連項目

- [混在 (ネイティブおよびマネージド) アセンブリ](../dotnet/mixed-native-and-managed-assemblies.md)
