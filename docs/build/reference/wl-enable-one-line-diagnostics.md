---
title: /WL (1 行診断の有効化)
ms.date: 11/04/2016
f1_keywords:
- /wl
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
ms.openlocfilehash: b1ded1cd18eb75ed47b76c1353ad82a7fa497ba9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988569"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (1 行診断の有効化)

エラーメッセージまたは警告メッセージに追加情報を追加します。

## <a name="syntax"></a>構文

```
/WL
```

## <a name="remarks"></a>Remarks

C++コンパイラからのエラーメッセージと警告メッセージの後に、新しい行に既定で表示される追加情報を指定できます。 コマンドラインからコンパイルする場合、追加の情報行をエラーメッセージまたは警告メッセージに追加できます。 これは、ビルド出力をログファイルにキャプチャし、そのログを処理してすべてのエラーと警告を検索する場合に適しています。 セミコロンは、エラーまたは警告メッセージを追加行から分離します。

すべてのエラーメッセージと警告メッセージに追加の情報が含まれているわけではありません。 次のコードでは、追加情報行を含むエラーが生成されます。 **/WL**を使用すると、効果をテストすることができます。

```cpp
// compiler_option_WL.cpp
// compile with: /WL
#include <queue>
int main() {
   std::queue<int> q;
   q.fromthecontinuum();   // C2039
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. [追加のオプション] ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>参照

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
