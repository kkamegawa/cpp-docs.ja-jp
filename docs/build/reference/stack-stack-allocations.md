---
title: /STACK (スタック割り当て)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.StackReserveSize
- VC.Project.VCLinkerTool.StackCommitSize
- /stack
helpviewer_keywords:
- STACK linker option
- -STACK linker option
- memory allocation, stack
- /STACK linker option
- stack, setting size
ms.assetid: 73283660-e4bd-47cc-b5ca-04c5d739034c
ms.openlocfilehash: 27de554e1933b2753f641be358461c8d7ff4fffa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317927"
---
# <a name="stack-stack-allocations"></a>/STACK (スタック割り当て)

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Remarks

/STACK オプションは、スタックのサイズをバイト単位で指定します。 このオプションは、.exe ファイルのビルドだけに使用します。

`reserve` 値は、仮想メモリ内のスタック割り当ての合計サイズを指定します。 ARM、x86 および x64 マシン、既定のスタック サイズは 1 MB です。

`commit` は、オペレーティング システムによって解釈が異なります。 Windows WindowsRT では、一度に確保する物理メモリ量です。 仮想メモリがコミットされると、ページング ファイル内にメモリ空間が予約されます。 `commit` の値を大きく設定すると、アプリケーションに必要なスタック領域が増えたときに処理時間を節約できます。ただし、必要なメモリ量と起動時間が増えます。 ARM、x86 および x64 マシン、既定のコミット値は 4 KB です。

引数 `reserve` と引数 `commit` の値は、10 進表記か C 言語表記で指定します。

スタックのサイズを設定するもう 1 つの方法は、 [STACKSIZE](stacksize.md)モジュール定義 (.def) ファイル内のステートメント。 **STACKSIZE**オーバーライド スタック割り当て (/stack) オプションの両方が指定されている場合。 スタック サイズを変更するには、.exe ファイルを使用してビルドした後、 [EDITBIN](editbin-reference.md)ツール。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**リンカー**フォルダー。

1. 選択、**システム**プロパティ ページ。

1. 次のいずれかのプロパティを変更します。

   - **スタックのコミット サイズ**

   - **スタックのサイズ**

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> プロパティおよび <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A> プロパティを参照してください。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
