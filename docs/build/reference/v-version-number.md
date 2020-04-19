---
title: /V (バージョン番号)
ms.date: 11/04/2016
f1_keywords:
- /v
helpviewer_keywords:
- embedding version strings
- /V compiler option [C++]
- version numbers, specifying for .obj
- V compiler option [C++]
- -V compiler option [C++]
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
ms.openlocfilehash: 7bebd3ab9677bb340203bbf857e4ee9f287e36e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317316"
---
# <a name="v-version-number"></a>/V (バージョン番号)

非推奨。 .Obj ファイル内のテキスト文字列を埋め込みます。

## <a name="syntax"></a>構文

```
/Vstring
```

## <a name="arguments"></a>引数

*string*<br/>
.Obj ファイルに埋め込まれるバージョン番号または著作権情報を指定する文字列。

## <a name="remarks"></a>Remarks

.Obj ファイル バージョン番号と著作権文字列ラベルです。 文字列の一部である場合、スペースまたはタブ文字を二重引用符 (") で囲む必要があります。 円記号 (\\) の文字列の一部である場合、二重引用符を付ける必要があります。 間にスペース **/V**と`string`は省略可能です。

使用することも[コメント (C/C++)](../../preprocessor/comment-c-cpp.md)コンパイラの名前とバージョン番号を .obj ファイル配置コンパイラ コメントの型引数を持つ。

**/V**以降では、Visual Studio 2005; オプションは非推奨 **/V**は、主に仮想デバイス ドライバー (Vxd) の構築をサポートするために使用して、Vxd の構築は、Visual C ツールセットでサポートが不要になった。 非推奨のコンパイラ オプションの一覧は、次を参照してください。**非推奨とされた削除済みのコンパイラ オプション**で[Compiler Options Listed by Category](compiler-options-listed-by-category.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. **[追加のオプション]** ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
