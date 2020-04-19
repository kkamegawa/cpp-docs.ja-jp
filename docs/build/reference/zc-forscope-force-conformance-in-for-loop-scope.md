---
title: /Zc:forScope (for ループのスコープの強制準拠)
ms.date: 03/06/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope
- VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope
- /zc:forScope
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
ms.openlocfilehash: 7f98667d3a771994d1b4e54b429f42cb566c102c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316029"
---
# <a name="zcforscope-force-conformance-in-for-loop-scope"></a>/Zc:forScope (for ループのスコープの強制準拠)

Microsoft の拡張機能 ( [/Ze](../../cpp/for-statement-cpp.md) ) の[for](za-ze-disable-language-extensions.md)ループの標準 C++ 動作を実装するために使用します。

## <a name="syntax"></a>構文

> **/Zc:forScope**[**-**]

## <a name="remarks"></a>Remarks

標準動作とは、 **for** ループの初期化子が **for** ループの後にスコープ外に出るようにすることです。 **/Zc:forScope-** と [/Ze](za-ze-disable-language-extensions.md)では、 **for** ループの初期化子は、ローカル スコープが終わるまでスコープ内にとどまります。

**/Zc:forScope**オプションが既定でオンです。 **/Zc:forScope**ときに影響しません、 [/permissive -](permissive-standards-conformance.md)オプションを指定します。

**/Zc:forScope-** オプションは非推奨とされます。今後のバージョンからは削除されます。 **/Zc:forScope-** を使うと、廃止予定の警告 D9035 が表示されます。

次のコードは **/Ze** ではコンパイルされますが、 **/Za**ではコンパイルされません。

```cpp
// zc_forScope.cpp
// compile by using: cl /Zc:forScope- /Za zc_forScope.cpp
// C2065, D9035 expected
int main() {
    // Compile by using cl /Zc:forScope- zc_forScope.cpp
    // to compile this non-standard code as-is.
    // Uncomment the following line to resolve C2065 for /Za.
    // int i;
    for (int i = 0; i < 1; i++)
        ;
    i = 20;   // i has already gone out of scope under /Za
}
```

**/Zc:forScope-** を使う場合、以前のスコープで行った宣言によって変数がスコープ内にあるときに、警告 C4288 (既定ではオフ) が表示されます。 これを示すために、サンプル コードから `//` の文字を削除して `int i`を宣言します。

**/Zc:forScope** の実行時の動作は、 [conform](../../preprocessor/conform.md) プラグマを使って変更できます。

既存の .pch ファイルがあるプロジェクトで **/Zc:forScope-** を使う場合、警告が表示され、 **/Zc:forScope-** は無視され、既存の .pch ファイルを使ってコンパイルが継続されます。 新しい .pch ファイルを生成する場合は、使用[/Yc (プリコンパイル済みヘッダー ファイルの作成)](yc-create-precompiled-header-file.md)します。

Visual C++ の準拠に関する問題について詳しくは、「 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)」をご覧ください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **言語**プロパティ ページ。

1. **[for ループ スコープの強制準拠]** プロパティを変更します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A>

## <a name="see-also"></a>関連項目

[/Zc (準拠)](zc-conformance.md)<br/>
[/Za、/Ze (言語拡張機能の無効化)](za-ze-disable-language-extensions.md)<br/>
