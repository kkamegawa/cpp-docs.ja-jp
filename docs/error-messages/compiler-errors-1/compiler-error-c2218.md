---
title: コンパイラ エラー C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: 5a9d897686fc915c9892fa2bcd51fa3ca3c8b05e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165678"
---
# <a name="compiler-error-c2218"></a>コンパイラ エラー C2218

'__vectorcall' と '/arch:IA32' は同時に使用できません

`__vectorcall` の呼び出し規約は、ストリーミング SIMD 拡張命令 2 (SSE2) 以上が搭載された x86 および x64 プロセッサのネイティブ コードでのみサポートされます。 詳細については、次を参照してください。 [_ _vectorcall](../../cpp/vectorcall.md)します。

このエラーを修正するには、SSE2、AVX、または AVX2 をターゲットにするようにコンパイラ オプションを変更します。 詳細については、「[/arch (x86)](../../build/reference/arch-x86.md)」を参照してください。