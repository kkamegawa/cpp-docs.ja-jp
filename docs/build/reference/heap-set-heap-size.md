---
title: /HEAP (ヒープ サイズの設定)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- /heap
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: 715eaa358d052d4ae646f38f2e784f0235dffccb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270355"
---
# <a name="heap-set-heap-size"></a>/HEAP (ヒープ サイズの設定)

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>Remarks

/HEAP オプションは、ヒープのサイズをバイト単位で設定します。 このオプションは、.exe ファイルを作成するときにのみで使用します。

*予約*引数は、仮想メモリのヒープ割り当ての合計を指定します。 既定のヒープ サイズは、1 MB です。 リンカーは、最も近い 4 バイトに指定した値を丸めます。

省略可能な`commit`引数を一度に割り当てる物理メモリの量を指定します。 仮想メモリがコミットされると、ページング ファイル内にメモリ空間が予約されます。 高度な`commit`値は、アプリケーションが、ヒープ領域を増やす必要がありますが、メモリの量と起動時間が増加時間を保存します。

指定、*予約*と`commit`10 進数または C 言語表記の値。

この機能を利用し、モジュール定義ファイルも[HEAPSIZE](heapsize.md)します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**システム**プロパティ ページ。

1. 変更、**ヒープ コミット サイズ**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 「 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> 」および「 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>」を参照してください。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
