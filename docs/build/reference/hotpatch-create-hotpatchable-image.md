---
title: /hotpatch (ホットパッチ可能なイメージの作成)
ms.date: 11/12/2018
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
ms.openlocfilehash: 8830b26b8fdfc3db2aa5fe31a52e6226fd554946
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291653"
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (ホットパッチ可能なイメージの作成)

イメージをホットパッチできるようにします。

## <a name="syntax"></a>構文

```
/hotpatch
```

## <a name="remarks"></a>Remarks

ときに **/hotpatch**されるコンパイルで、コンパイラは、各関数の最初の命令が、ホットパッチに必要な 2 バイト以上であること。

使用した後、イメージのホットパッチを行うための準備を完了する **/hotpatch**使用する必要がありますをコンパイルする[/FUNCTIONPADMIN (ホットパッチ可能なイメージの作成)](functionpadmin-create-hotpatchable-image.md)にリンクします。 コンパイルし、cl.exe の 1 つの呼び出しを使用して、イメージを関連付ける **/hotpatch**意味 **/functionpadmin**します。

手順については、常に 2 バイトであるため、ARM アーキテクチャでより大きいまたは、x64 コンパイルは常に扱われます場合と **/hotpatch**指定されているを指定する必要はありません **/hotpatch**ときにこれらのターゲットのコンパイルします。ただし、するを使用してリンクする必要がありますも **/functionpadmin**にそれらのホットパッチ可能なイメージを作成します。 **/Hotpatch**コンパイラ オプションのみに影響を与えます x86 コンパイルします。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、 **C/C++** フォルダー。

1. 選択、**コマンドライン**プロパティ ページ。

1. コンパイラ オプションを追加、**追加オプション**ボックス。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
