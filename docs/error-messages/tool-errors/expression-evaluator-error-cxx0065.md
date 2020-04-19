---
title: 式エバリュエーター エラー CXX0065
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: 7b62e42da2a74d910e2dc56ce2dfcb5cb38f2bfa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299323"
---
# <a name="expression-evaluator-error-cxx0065"></a>式エバリュエーター エラー CXX0065

変数には、スタック フレームが必要です。

式には、現在のスコープ内に存在しますが、まだ作成されていない変数が含まれています。

このエラーは、関数がまだを設定するには関数のスタック フレームのプロローグにステップ インする場合、または関数の終了コードにステップ インする場合に発生することができます。

式を評価する前に設定されているスタック フレームまでプロローグ コードをステップ実行します。

このエラーは、can0065 と同じものと同じです。