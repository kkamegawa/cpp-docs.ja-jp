---
title: MMWORD
ms.date: 12/17/2019
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: fd3b9f40b7ff9fa4dae570e0ed906c13a9456424
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75311924"
---
# <a name="mmword"></a>MMWORD

MMX および SSE (XMM) 命令で64ビットのマルチメディアオペランドに使用されます。

## <a name="syntax"></a>構文

> **MMWORD**

## <a name="remarks"></a>コメント

**Mmword**は型です。  **Mmword**が MASM に追加される前に、同等の機能がによって実現されました。

```asm
    mov mm0, qword ptr [ebx]
```

どちらの命令も64ビットオペランドで動作しますが、 **QWORD**は64ビット符号なし整数の型であり、 **mmword**は64ビットマルチメディア値の型です。

**Mmword**は[__m64](../../cpp/m64.md)と同じ型を表すことを目的としています。

## <a name="example"></a>使用例

```asm
    movq     mm0, mmword ptr [ebx]
```

## <a name="see-also"></a>参照

[MASM BNF 文法](masm-bnf-grammar.md)
