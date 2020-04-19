---
title: コンパイラ エラー C2410
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: 8b01a2f7b9c55fb57c880df5033538f4e45f76b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282327"
---
# <a name="compiler-error-c2410"></a>コンパイラ エラー C2410

'identifier': 'context' であいまいなメンバー名

識別子は、1 つ以上の構造体またはこのコンテキストで共用体のメンバーです。

エラーの原因となったオペランドでは、構造体または共用体の指定子を使用します。 構造体または共用体の指定子は、型の識別子`struct`または`union`(、`typedef`名または構造体または共用体が参照されていると同じ型の変数)。 指定子は、オペランドを使用する最初のメンバー選択演算子 (.) の左のオペランドである必要があります。