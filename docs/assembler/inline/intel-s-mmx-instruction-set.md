---
title: Intel&#39;s MMX 命令セット
ms.date: 08/30/2018
ms.topic: reference
helpviewer_keywords:
- MMX instruction set
ms.assetid: 705deb2d-c3fd-4696-9e22-8bcf25866daf
ms.openlocfilehash: b8b2697fa106506dadfdaa96149fd6b0b093c844
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65445874"
---
# <a name="intel39s-mmx-instruction-set"></a>Intel&#39;s MMX 命令セット

**Microsoft 固有の仕様**

MicrosoftC++コンパイラでは、Intel の MMX (マルチ メディア拡張機能) の命令が、インライン アセンブラーのセットを使用できます。 MMX 命令は、デバッガーの逆アセンブリによってもサポートされます。 関数は、MMX 命令が含まれていますが、マルチ メディアの状態を空に EMMS 命令が含まれていない場合、コンパイラは警告メッセージを生成します。 詳細については、Intel の Web サイトを参照してください。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__asm ブロックでのアセンブリ言語の使用](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>