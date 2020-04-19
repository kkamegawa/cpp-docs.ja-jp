---
title: コンパイラの警告 (レベル 4) C4510
description: コンパイラの警告 C4510 の説明と解決策。
ms.date: 09/22/2019
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: 05a6d0fe42d8247d3328506d8772b2fa77b5703c
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230382"
---
# <a name="compiler-warning-level-4-c4510"></a>コンパイラの警告 (レベル 4) C4510

> '*class*': 既定のコンストラクターを生成できませんでした

コンパイラは、ユーザー定義のコンストラクターを持たない、指定されたクラスの既定のコンストラクターを生成できません。 この型のオブジェクトは作成できません。

次のように、コンパイラが既定のコンストラクターを生成しないようにする状況がいくつかあります。

- **Const**データメンバー。

- 参照であるデータメンバー。

この問題を解決するには、これらのメンバーを初期化するクラスのユーザー定義の既定のコンストラクターを作成します。
