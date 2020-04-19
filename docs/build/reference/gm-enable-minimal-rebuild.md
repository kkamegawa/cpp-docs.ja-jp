---
title: /Gm (簡易リビルドの有効化)
ms.date: 11/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- /FD
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 4a66dda37b84119a4b8bc23f7fc719d50e8786f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292069"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (簡易リビルドの有効化)

非推奨。 最小リビルドを有効にします。最小リビルドにより、(ヘッダー (.h) ファイルに格納されている) 変更された C++ クラス定義を含む C++ ソース ファイルを再コンパイルする必要があるかどうかが決定されます。

## <a name="syntax"></a>構文

```
/Gm
```

## <a name="remarks"></a>Remarks

**/Gm**は非推奨とされます。 ヘッダー ファイルの変更の特定の種類のビルドがありません。 このオプションは、プロジェクトから安全に削除できます。 ビルド時間を向上させるのには、プリコンパイル済みヘッダーを使用して、増分、並列のオプションを代わりにビルドを勧めします。 非推奨のコンパイラ オプションの一覧は、次を参照してください。、**非推奨とされた削除済みのコンパイラ オプション**セクション[Compiler Options Listed by Category](compiler-options-listed-by-category.md)します。

最初のコンパイル時に、コンパイラによってソース ファイルとクラス定義の間の依存関係情報がプロジェクトの .idb ファイルに格納されます。 (依存関係情報は、どのソース ファイルがどのクラス定義に依存するように指示およびにあるどの .h ファイルに定義します。)それ以降のコンパイルでは、.idb ファイルに格納されている情報を使用して、変更された .h ファイルが含まれている場合でも、コンパイルするソース ファイルが必要かどうかを判断します。

> [!NOTE]
> 最小リビルドは、クラス定義がインクルード ファイル間で変わらないことに依存します。 .idb ファイル内の依存関係情報はプロジェクト全体に対して作成されるため、クラス定義はプロジェクトに対してグローバルである必要があります (特定のクラスの定義は 1 つのみである必要があります)。 プロジェクト内のクラスに複数の定義がある場合は、最小リビルドを無効にします。

Incremental linker を使用して、.obj ファイルに含まれる Windows メタデータをサポートしていないため、 [/ZW (Windows ランタイムのコンパイル)](zw-windows-runtime-compilation.md)オプション、 **/Gm**オプションと互換性がない **/ZW**します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **コード生成**プロパティ ページ。

1. 変更、**最小リビルドを有効にする**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
