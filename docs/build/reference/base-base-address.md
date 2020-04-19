---
title: /BASE (ベース アドレス)
ms.date: 09/05/2018
f1_keywords:
- /base
- VC.Project.VCLinkerTool.BaseAddress
helpviewer_keywords:
- base addresses [C++]
- programs [C++], preventing relocation
- semicolon [C++], specifier
- -BASE linker option
- key address size
- environment variables [C++], LIB
- programs [C++], base address
- LIB environment variable
- BASE linker option
- DLLs [C++], linking
- /BASE linker option
- '@ symbol for base address'
- executable files [C++], base address
- at sign symbol for base address
ms.assetid: 00b9f6fe-0bd2-4772-a69c-7365eb199069
ms.openlocfilehash: dc6380903af0be2e6696ca3589813c249f71dd05
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341022"
---
# <a name="base-base-address"></a>/BASE (ベース アドレス)

プログラムのベース アドレスを指定します。

## <a name="syntax"></a>構文

> **/BASE:**{*address*[**,**<em>size</em>] | **\@**<em>filename</em>**,**<em>key</em>}

## <a name="remarks"></a>Remarks

> [!NOTE]
> セキュリティ上の理由から、使用するをお勧めします。、 [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)実行可能ファイルのベース アドレスを指定する代わりにオプション。 これには、ランダムに再ベースできる読み込み時に Windows のアドレス空間レイアウト randomization (ASLR) 機能を使用して実行可能イメージが生成されます。 /DYNAMICBASE オプションが既定でオンにします。

/、基本オプションは、.exe ファイルまたは DLL ファイルの既定の場所をオーバーライドして、プログラムのベース アドレスを設定します。 .Exe ファイルの既定のベース アドレスは、32 ビット イメージの 0x400000 または 64 ビット イメージの 0x140000000 は。 Dll の場合、既定のベース アドレスは、32 ビット イメージの 0x10000000 または 64 ビット イメージの 0x180000000 します。 アドレス空間レイアウト randomization (ASLR) をサポートしていないか、/DYNAMICBASE:NO オプションが設定されたオペレーティング システムでオペレーティング システムは、最初に、指定したプログラムまたは既定のベース アドレスをロードを試みます。 十分な空き領域がない場合は使用可能なシステムには、プログラムが再配置します。 再配置を防ぐためには、使用、 [/fixed](fixed-fixed-base-address.md)オプション。

場合、リンカーはエラーを発行*アドレス*64 K の倍数ではありません。 必要に応じて、プログラムのサイズを指定することができます。リンカーは、プログラムが指定したサイズに収まらない場合に警告を発行します。

コマンド ラインでベース アドレスの応答ファイルを使用してベース アドレスを指定する別の方法です。 ベース アドレスの応答ファイルは、ベース アドレスと、プログラムで使用すると、すべての Dll は、各ベース アドレスに対して一意のテキストのキーの省略可能なサイズを含むテキスト ファイルです。 応答ファイルを使用してベース アドレスを指定するには、使用、アット マーク (**\@**) 後に、応答ファイルの名前*filename*、コンマ、その後に、*キー*ファイルで使用するベース アドレスの値。 リンカー *filename*か、指定されたパスのパスが指定されていない場合、LIB 環境変数で指定されたディレクトリでします。 内の各行*filename* 1 つの DLL を表し、次の構文します。

> *キー* *アドレス*[*サイズ*] **;** *コメント*

*キー*英数字の文字列は、大文字小文字は区別されません。 通常、DLL の名前が必要はありません。 *キー*ベースが続く*アドレス*C 言語、16 進数、または 10 進表記で、省略可能な最大*サイズ*します。 3 つの引数は、スペースまたはタブで区切られます。 場合、リンカーが警告を発行した*サイズ*は、プログラムに必要な仮想アドレス空間よりも少ない。 A*コメント*をセミコロンで指定された (**;**)、同一または別の行を指定できます。 リンカーでは、行の末尾にセミコロンからすべてのテキストは無視されます。 この例では、このようなファイルの一部を示します。

```
main   0x00010000    0x08000000    ; for PROJECT.exe
one    0x28000000    0x00100000    ; for DLLONE.DLL
two    0x28100000    0x00300000    ; for DLLTWO.DLL
```

これらの行を含むファイルには、DLLS.txt を呼び出すと、次のコマンドの例には、この情報が適用されます。

```
link dlltwo.obj /dll /base:@dlls.txt,two
```

ベース アドレスを設定する別の方法を使用して、*基本*で引数を[名前](name-c-cpp.md)または[ライブラリ](library.md)ステートメント。 /Baseaddress と[/DLL](dll-build-a-dll.md)オプションはまとめてと同じですが、**ライブラリ**ステートメント。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **リンカー** > **詳細**プロパティ ページ。

1. 変更、**ベース アドレス**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
