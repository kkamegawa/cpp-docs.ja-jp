---
title: /DEFAULTLIB (既定のライブラリの指定)
ms.date: 05/29/2018
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
ms.openlocfilehash: 0b7d4569c7be70bd97094ebbe09a7ae462331983
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293863"
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (既定のライブラリの指定)

外部参照を解決するために検索する既定のライブラリを指定します。

## <a name="syntax"></a>構文

> **/DEFAULTLIB**:_ライブラリ_

### <a name="arguments"></a>引数

*ライブラリ*<br/>
外部参照を解決するときに検索するライブラリの名前。

## <a name="remarks"></a>Remarks

**/DEFAULTLIB**オプションでは、1 つ追加*ライブラリ*リンクが参照を解決するときに検索するライブラリの一覧にします。 指定されているライブラリ **/DEFAULTLIB**後コマンドラインで、既定のライブラリが .obj ファイル内の前に明示的に指定したライブラリが検索されます。

引数を指定せずに使用すると、 [/NODEFAULTLIB (すべて既定のライブラリの無視)](nodefaultlib-ignore-libraries.md)オプションをすべてオーバーライドされます **/DEFAULTLIB**:*ライブラリ*オプション。 **/NODEFAULTLIB**:*ライブラリ*上書きオプション **/DEFAULTLIB**:*ライブラリ*ときに、同じ*ライブラリ*両方で名前を指定します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **リンカー** > **コマンドライン**プロパティ ページ。

1. **追加オプション**、入力、 **/DEFAULTLIB**:*ライブラリ*を検索するには、各ライブラリのオプション。 **OK** を選択して変更を保存してください。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

- [MSVC リンカーのリファレンス](linking.md)
- [MSVC リンカー オプション](linker-options.md)
