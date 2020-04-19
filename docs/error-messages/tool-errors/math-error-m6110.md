---
title: 数値演算エラー M6110
ms.date: 11/04/2016
f1_keywords:
- M6110
helpviewer_keywords:
- M6110
ms.assetid: aac9ae37-6a6d-46e9-85d4-dfe03f1c3e11
ms.openlocfilehash: d56326c0daa326ef832eb81024850d6ef06f5649
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393260"
---
# <a name="math-error-m6110"></a>数値演算エラー M6110

スタック オーバーフロー

浮動小数点式には、浮動小数点スタック オーバーフローが発生します。

浮動小数点例外のスタック オーバーフローは、8087/287/387 コプロセッサでサポートされる、通常、8 つのレベルだけでなく、7 つのレベルの上限に達するまでにトラップされます。

終了コード 138 でプログラムを終了します。