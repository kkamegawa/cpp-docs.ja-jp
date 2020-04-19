---
title: コンパイラの警告 (レベル 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: b799c568d73a081a4d4cf5616f376f3efc9eeffb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349673"
---
# <a name="compiler-warning-level-4-c4611"></a>コンパイラの警告 (レベル 4) C4611

'function' と C++ オブジェクト デストラクション間の相互作用はポータブルでないです。

関数が含まれる一部のプラットフォームで**キャッチ**スコープ外の時の破棄の C++ オブジェクト セマンティクスをサポートしていません。

予期しない動作を回避するには、使用しないように**キャッチ**をコンス トラクターとデストラクターを持つ関数でします。

この警告は 1 回だけです。参照してください[pragma 警告](../../preprocessor/warning.md)します。