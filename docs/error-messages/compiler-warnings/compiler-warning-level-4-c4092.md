---
title: コンパイラの警告 (レベル 4) C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: a6949586cf3faa00aafed37a72e58c1b80266cf5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401385"
---
# <a name="compiler-warning-level-4-c4092"></a>コンパイラの警告 (レベル 4) C4092

sizeof 演算子が 'unsigned long'。

オペランド、`sizeof`演算子が非常に多いため、`sizeof`符号なしで返される**long**します。 Microsoft 拡張機能でこの警告が発生します ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。 ANSI 互換 (/Za) では、代わりに、結果が切り捨てられます。