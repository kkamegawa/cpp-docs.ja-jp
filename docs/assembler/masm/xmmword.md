---
title: XMMWORD
ms.date: 12/17/2019
f1_keywords:
- XMMWORD
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
ms.openlocfilehash: 1116729883bf9b1b9342b30332bab5de6ba59015
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75319113"
---
# <a name="xmmword"></a>XMMWORD

MMX および SSE (XMM) 命令で128ビットのマルチメディアオペランドに使用されます。

## <a name="syntax"></a>構文

> **XMMWORD**

## <a name="remarks"></a>コメント

**Xmmword**は[__m128](../../cpp/m128.md)と同じ型を表すことを目的としています。

## <a name="example"></a>使用例

```asm
    movdqa   xmm0, xmmword ptr [ebx]
```

## <a name="see-also"></a>参照

[MASM BNF 文法](masm-bnf-grammar.md)
