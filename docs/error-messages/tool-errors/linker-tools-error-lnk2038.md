---
title: リンカ ツール エラー LNK2038
ms.date: 12/15/2017
f1_keywords:
- LNK2038
helpviewer_keywords:
- LNK2038
ms.openlocfilehash: f2839494232e7b57325b6f7abb960a258ba13078
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446954"
---
# <a name="linker-tools-error-lnk2038"></a>リンカ ツール エラー LNK2038

> 不一致が検出されました '*名前*': 値'*value_1*'値と一致しない'*value_2*' で *<filename.obj>。*

シンボルの不一致がリンカーによって検出されました。 このエラーは、アプリへのリンクが競合するシンボル定義を使用して、ライブラリまたは他のオブジェクトを含む、アプリのさまざまな部分のコードを示します。 [の不一致を検出](../../preprocessor/detect-mismatch.md)プラグマを使用して、このようなシンボルを定義し、競合する値を検出します。

## <a name="possible-causes-and-solutions"></a>考えられる原因と解決策

このエラーは、プロジェクトのオブジェクト ファイルが古い形式のときに発生する可能性があります。 このエラーに対して他のソリューションを実行する前に、オブジェクト ファイルが最新であることを検証するために、クリーン ビルドを実行してください。

Visual Studio は、実行時エラーまたはその他の予測できない動作を発生させる可能性のある互換性のないコードのリンクを防ぐために、次のシンボルを定義します。

- `_MSC_VER` Microsoft のメジャーおよびマイナー バージョン番号を示すC++コンパイラ (MSVC) アプリまたはライブラリを構築するために使用します。 MSVC の 1 つのバージョンを使用してコンパイルされたコードは、別のメジャーおよびマイナー バージョン番号のあるバージョンを使用してコンパイルされたコードと互換性がありません。 詳細については、次を参照してください。`_MSC_VER`で[定義済みマクロ](../../preprocessor/predefined-macros.md)します。

   を使用していると、取得またはライブラリの互換性のあるバージョンをビルドすることはできませんが、MSVC のバージョンと互換性がないライブラリをリンクする場合は、プロジェクトをビルドする以前のバージョンのコンパイラを使用できます。 変更、 **プラットフォーム ツールセット**以前のツールセットにプロジェクトのプロパティ。 詳細については、「[方法 :ターゲット フレームワークおよびプラットフォームのツールセットを変更する](../../build/how-to-modify-the-target-framework-and-platform-toolset.md)」を参照してください。

- `_ITERATOR_DEBUG_LEVEL` セキュリティ機能とデバッグ、C++ 標準ライブラリで有効になっている機能のレベルを示します。 これらの機能は、特定の C++ 標準ライブラリのオブジェクトの表示を変更できるため、こうしたオブジェクトは、異なるセキュリティ機能とデバッグ機能を使用するオブジェクトと互換性がなくなります。 詳細については、「[_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md)」を参照してください。

- `RuntimeLibrary` アプリまたはライブラリで使用される C++ 標準ライブラリと C ランタイムのバージョンを示します。 C++ 標準ライブラリまたは C ランタイムの 1 種類のバージョンを使用するコードは、異なるバージョンを使用するコードと互換性がありません。 詳細については、「[/MD、/MT、/LD (ランタイム ライブラリの使用)](../../build/reference/md-mt-ld-use-run-time-library.md)」を参照してください。

- `_PPLTASKS_WITH_WINRT` そのコードを使用することを示します、[並列パターン ライブラリ (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)のさまざまな設定を使用してコンパイルされたオブジェクトにリンクされて、 [/ZW](../../build/reference/zw-windows-runtime-compilation.md)コンパイラ オプション。 (**/ZW**サポートC++/CX)。同じを使用して使用したり、PPL に依存するコードをコンパイルする必要があります **/ZW**アプリの残りの部分で使用される設定。

これらのシンボルの値が、Visual Studio ソリューションのプロジェクト全体で一貫していることと、使用中のアプリがリンクしているコードとライブラリに一致していることを確認してください。

## <a name="third-party-library-issues-and-vcpkg"></a>サード パーティ製のライブラリの問題と Vcpkg

ビルドの一部として、サード パーティ製ライブラリを構成しようとしているときにこのエラーが発生する場合は、使用を検討して[Vcpkg](../../vcpkg.md)ビジュアルの C++ パッケージ マネージャーをインストールして、ライブラリをビルドします。 Vcpkg のサポートが増加し続ける[サード パーティ製ライブラリの一覧](https://github.com/Microsoft/vcpkg/tree/master/ports)、およびすべての構成プロパティと、プロジェクトの一部として、成功したビルドに必要な依存関係を設定します。 詳細については、関連するを参照してください[Visual C ブログ](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/)を投稿します。

## <a name="see-also"></a>関連項目

[リンカー ツール エラーと警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)