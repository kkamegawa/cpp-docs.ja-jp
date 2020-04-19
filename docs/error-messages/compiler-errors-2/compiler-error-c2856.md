---
title: コンパイラ エラー C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: 1e515f250c8ab9d1008ded91b99176f1d86d7cd1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406848"
---
# <a name="compiler-error-c2856"></a>コンパイラ エラー C2856

\#プラグマ hdrstop は #if ブロックの内部ですることはできません。

`hdrstop`プラグマは、条件付きコンパイル ブロックの本文内に配置することはできません。

移動、`#pragma hdrstop`ステートメントに含まれていない領域に、`#if/#endif`ブロックします。