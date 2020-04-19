---
title: /DISASM
ms.date: 01/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: fb394b2266470e77c50ce5398aea961c37ac34fb
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927718"
---
# <a name="disasm"></a>/DISASM

DUMPBIN 出力のコードセクションの逆アセンブリを出力します。

## <a name="syntax"></a>構文

> **/DISASM**{ **:** \[**BYTES**NOBYTES]}|

### <a name="arguments"></a>引数

**BYTES**<br/>
命令バイトを、解釈されたオペコードおよび逆アセンブリ出力の引数と共に含めます。 既定のオプションです。

**NOBYTES**<br/>
には、逆アセンブリ出力に命令バイトが含まれていません。

## <a name="remarks"></a>Remarks

**/Disasm**オプションは、ファイルのコードセクションの逆アセンブリを表示します。 デバッグシンボルがファイル内に存在する場合は、これを使用します。

**/Disasm**は、ネイティブで管理されていないイメージでのみ使用する必要があります。 マネージコードに相当するツールは、 [ildasm.exe](/dotnet/framework/tools/ildasm-exe-il-disassembler)です。

[/Gl (プログラム全体の最適化)](gl-whole-program-optimization.md)コンパイラオプションで生成されたファイルで使用できるのは、 [/HEADERS](headers.md) DUMPBIN オプションだけです。

## <a name="see-also"></a>関連項目

[DUMPBIN オプション](dumpbin-options.md)
