---
title: コンパイラ エラー C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: 340a5d0596160b6c9c7bcfc78aed812f8c5f3fa3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367604"
---
# <a name="compiler-error-c2696"></a>コンパイラ エラー C2696

管理対象の型 'type' の一時オブジェクトを作成することはできません。

参照`const`アンマネージ プログラムが、コンパイラはコンス トラクターを呼び出すし、スタック上に一時オブジェクトを作成します。 ただし、マネージ クラスはスタックで作成できません。

C2696 は古い形式のコンパイラ オプションを使用して到達のみ **/clr:oldSyntax**します。
