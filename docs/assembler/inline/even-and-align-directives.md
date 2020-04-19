---
title: EVEN および ALIGN ディレクティブ
ms.date: 08/30/2018
f1_keywords:
- align
- EVEN
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
ms.openlocfilehash: 522d5689d680d0fc334743d2802abe21570dd6f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167320"
---
# <a name="even-and-align-directives"></a>EVEN および ALIGN ディレクティブ

**Microsoft 固有の仕様**

では、インライン アセンブラーがほとんどの MASM ディレクティブをサポートしていませんが`EVEN`と**ALIGN**します。 これらのディレクティブを配置**NOP** (操作なし)」の手順には、アセンブリのコードを特定の境界にラベルを配置するために必要とします。 これにより、一部のプロセッサの命令フェッチ操作がより効率的にします。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__asm ブロックでのアセンブリ言語の使用](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>