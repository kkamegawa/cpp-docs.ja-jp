---
title: /NODEFAULTLIB (ライブラリを無視する)
ms.date: 03/26/2019
f1_keywords:
- VC.Project.VCLinkerTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLinkerTool.OVERWRITEDefaultLibraryNames
- /nodefaultlib
helpviewer_keywords:
- default libraries, removing
- -NODEFAULTLIB linker option
- libraries, ignore
- NODEFAULTLIB linker option
- /NODEFAULTLIB linker option
- ignore libraries linker option
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
ms.openlocfilehash: 24528eb4c387c4cd0921ab089370d72b076ad640
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320520"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB (ライブラリを無視する)

> **/NODEFAULTLIB**[__:__*library*]

## <a name="arguments"></a>引数

*ライブラリ*<br/>
外部参照を解決するときに無視するライブラリ。

## <a name="remarks"></a>Remarks

/NODEFAULTLIB オプションは、外部参照を解決するときに検索するライブラリの一覧から 1 つまたは複数の既定のライブラリを削除するリンカーに指示します。

既定のライブラリへの参照が含まれていない .obj ファイルを作成するには、使用[/Zl (既定ライブラリ名の省略)](zl-omit-default-library-name.md)します。

既定では、/NODEFAULTLIB は外部参照を解決するときに検索するライブラリの一覧から既定ライブラリをすべて削除します。 省略可能な*ライブラリ*パラメーターを使用して、外部参照を解決するときに検索するライブラリの一覧から指定したライブラリを削除できます。 /NODEFAULTLIB オプションを除外する各ライブラリの 1 つを指定します。

リンカーを明示的に指定すると、その後で指定したライブラリの既定のライブラリを最初に検索して外部定義への参照を解決、 [/DEFAULTLIB:](defaultlib-specify-default-library.md)オプション、し、既定のライブラリという名前の .obj とファイル。

/NODEFAULTLIB:*ライブラリ*/DEFAULTLIB よりも優先されます:*ライブラリ*とき同じ*ライブラリ*両方で名前が指定されています。

/NODEFAULTLIB を使用して C ランタイム ライブラリなし、プログラムをビルドする場合にも使用して、必要に応じて[/ENTRY](entry-entry-point-symbol.md)をプログラムで、エントリ ポイント関数を指定します。 詳しくは、「[CRT ライブラリの機能](../../c-runtime-library/crt-library-features.md)」をご覧ください。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **リンカー** > **入力**プロパティ ページ。

1. 選択、**すべて既定のライブラリの無視**プロパティ。 またはで無視するライブラリのセミコロン区切りのリストを指定、**特定の既定のライブラリの無視**プロパティ。 **コマンドライン**プロパティ ページは、これらのプロパティに加えた変更の効果を示しています。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 「 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> 」および「 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>」を参照してください。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
