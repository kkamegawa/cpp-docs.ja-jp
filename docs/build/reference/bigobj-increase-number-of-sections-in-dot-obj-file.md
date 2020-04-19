---
title: /bigobj (.obj ファイル内のセクションの数を増やす)
ms.date: 03/26/2019
f1_keywords:
- /bigobj
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
ms.openlocfilehash: 30c02c72496e3bb91da3b39e1870f1dc5a2c040a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493113"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (.obj ファイル内のセクションの数を増やす)

**/bigobj**は、オブジェクトファイルに含めることができるセクションの数を増やします。

## <a name="syntax"></a>構文

> **/bigobj**

## <a name="remarks"></a>Remarks

既定では、オブジェクトファイルは、最大 65279 (約 2 ^ 16) のアドレス指定可能なセクションを保持できます。 この制限は、どのターゲットプラットフォームが指定されているかに関係なく適用されます。 **/bigobj**は、そのアドレス容量を 4294967296 (2 ^ 32) に増やします。

ほとんどのモジュールでは、65279を超えるセクションを含む .obj ファイルは生成されません。 ただし、コンピューターによって生成されるコード、またはテンプレートライブラリを多用するコードでは、より多くのセクションを保持できる .obj ファイルが必要になる場合があります。 コンピューターで生成された XAML コードに含まれるヘッダーの数が多いため、ユニバーサル Windows プラットフォーム (UWP) プロジェクトでは、 **/bigobj**が既定で有効になっています。 UWP アプリプロジェクトでこのオプションを無効にすると、コードによってコンパイラエラー C1128 が生成される場合があります。

PE COFF オブジェクトファイル形式の詳細については、Windows ドキュメントの「 [Pe 形式](/windows/win32/debug/pe-format)」を参照してください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[構成プロパティ]**  >  **[C/C++]**  >  **[コマンド ライン]** プロパティ ページを選択します。

1. **[追加オプション]** ボックスに、「 **/bigobj** 」コンパイラオプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
