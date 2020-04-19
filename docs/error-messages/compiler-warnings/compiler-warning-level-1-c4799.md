---
title: コンパイラの警告 (レベル 1) C4799
ms.date: 11/04/2016
f1_keywords:
- C4799
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
ms.openlocfilehash: 475451b47d461e7ea1428eb715a876fb023694d1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152217"
---
# <a name="compiler-warning-level-1-c4799"></a>コンパイラの警告 (レベル 1) C4799

> 関数の最後にない EMM '*関数*'

関数が少なくとも 1 つの MMX 命令がありません、`EMMS`命令。 マルチ メディアの命令を使用するときに、`EMMS`命令または`_mm_empty`組み込みを使用することも MMX コードの最後に、マルチ メディア タグ単語をオフにします。

返す前に EMMS 命令 ivec.h、コードが正しく使用しないことを使用して実行時に、C4799 を取得可能性があります。 これらのヘッダーに対する警告を false になります。 オフ ivec.h で _SILENCE_IVEC_C4799 を定義することで、これらに可能性があります。 ただし、この型の正しい警告コンパイラこの保持されることもあります。

関連情報については、次を参照してください。 [Intel の MMX の命令セット](../../assembler/inline/intel-s-mmx-instruction-set.md)します。