---
title: /Gh (_penter フック関数の有効化)
ms.date: 11/04/2016
f1_keywords:
- _penter
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
ms.openlocfilehash: bf7734a7b81c9550c060d43c2eabf5cb05332407
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292586"
---
# <a name="gh-enable-penter-hook-function"></a>/Gh (_penter フック関数の有効化)

呼び出し、`_penter`すべてのメソッドまたは関数の開始時の関数。

## <a name="syntax"></a>構文

```
/Gh
```

## <a name="remarks"></a>Remarks

`_penter`関数は、任意のライブラリの一部ではないの定義を提供するかどうかは`_penter`します。

明示的に呼び出す予定がない限り`_penter`プロトタイプを提供する必要はありません。 関数は、次のプロトタイプがあった場合とおよびエントリのすべてのレジスタのコンテンツをプッシュし、終了時に変更されていないコンテンツを表示にする必要がありますに記述する必要があります。

```
void __declspec(naked) __cdecl _penter( void );
```

この宣言は、64 ビットのプロジェクトで使用可能ではありません。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. **[追加のオプション]** ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="example"></a>例

コンパイルした場合、次のコード **/Gh**、表示方法`_penter`2 回; と呼ばれる関数を入力するときに 1 回`main`関数を入力するときに 1 回`x`。

```cpp
// Gh_compiler_option.cpp
// compile with: /Gh
// processor: x86
#include <stdio.h>
void x() {}

int main() {
   x();
}

extern "C" void __declspec(naked) __cdecl _penter( void ) {
   _asm {
      push eax
      push ebx
      push ecx
      push edx
      push ebp
      push edi
      push esi
    }

   printf_s("\nIn a function!");

   _asm {
      pop esi
      pop edi
      pop ebp
      pop edx
      pop ecx
      pop ebx
      pop eax
      ret
    }
}
```

```Output
In a function!
In a function!
```

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
