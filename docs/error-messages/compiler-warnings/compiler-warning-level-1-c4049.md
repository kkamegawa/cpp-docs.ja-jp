---
title: コンパイラの警告 (レベル 1) C4049
ms.date: 11/04/2016
f1_keywords:
- C4049
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
ms.openlocfilehash: a4958bb446b5f7e80ef2eef92b52a0f86cf6a134
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388764"
---
# <a name="compiler-warning-level-1-c4049"></a>コンパイラの警告 (レベル 1) C4049

コンパイラの制限: 行番号の出力を終了しています

ファイルに含まれる複数の 16,777, 215 (2<sup>24</sup>-1) ソース行。 コンパイラは、連番が 16,777, 215 を停止します。

16,777, 215 の行の後のコード。

- イメージには、行番号のデバッグ情報はありません。

- いくつかの診断は、不適切な行番号で報告されること可能性があります。

- .asm 一覧 (/FAs) が正しくない行の番号があります。