---
title: コンパイラ エラー C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a128613cabb201142c29b833959924dbf8a6e0ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160958"
---
# <a name="compiler-error-c2708"></a>コンパイラ エラー C2708

'identifier': 実パラメーターの長さ (バイト単位) は、前の呼び出しまたは参照によって異なります。

A [_ _stdcall](../../cpp/stdcall.md)関数プロトタイプの前が必要です。 それ以外の場合、コンパイラは、最初のプロトタイプとして関数呼び出しを解釈し、コンパイラと一致しない呼び出しを検出すると、このエラーが発生します。

修正するのには、このエラーは、関数プロトタイプを追加します。