---
title: コマンド ラインでのマニフェスト生成
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
ms.openlocfilehash: 381406213422e286dd9aba26adcdbd6caff7bfe3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493202"
---
# <a name="manifest-generation-at-the-command-line"></a>コマンド ラインでのマニフェスト生成

Nmake または同様C++のツールを使用してコマンドラインから C/アプリケーションをビルドする場合、マニフェストは、リンカーがすべてのオブジェクトファイルを処理し、最後のバイナリをビルドした後に生成されます。 リンカーは、オブジェクトファイルに格納されているアセンブリ情報を収集し、この情報を最終的なマニフェストファイルに結合します。 既定では、リンカーは*binary_name*という名前のファイルを生成します。最後のバイナリを記述する*拡張子*。 リンカーは、マニフェストファイルをバイナリ内に埋め込まず、マニフェストを外部ファイルとしてのみ生成できます。 マニフェスト[ツール (mt.exe)](/windows/win32/sbscs/mt-exe)を使用したり、マニフェストをリソースファイルにコンパイルしたりするなど、マニフェストを最終的なバイナリ内に埋め込むには、いくつかの方法があります。 これらの機能をインクリメンタルリンク、署名、エディットコンティニュとして有効にするために、マニフェストを最終的なバイナリ内に埋め込むときは、特定の規則に従う必要があることに注意してください。 これらのオプションとその他の[オプションについては、「方法:コマンドラインでビルドするときにC++ 、](how-to-embed-a-manifest-inside-a-c-cpp-application.md) C/アプリケーション内にマニフェストを埋め込みます。

## <a name="see-also"></a>関連項目

[マニフェスト](/windows/win32/sbscs/manifests)<br/>
[/INCREMENTAL (インクリメンタル リンクを行う)](reference/incremental-link-incrementally.md)<br/>
[厳密名アセンブリ (アセンブリ署名) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[エディット コンティニュ](/visualstudio/debugger/edit-and-continue)<br/>
[C/C++ プログラムのマニフェスト生成についての理解](understanding-manifest-generation-for-c-cpp-programs.md)<br/>
