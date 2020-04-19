---
title: 致命的なエラー C1311
ms.date: 11/04/2016
f1_keywords:
- C1311
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
ms.openlocfilehash: ba2b797c9bf521533e7c2ccff8d358b6216d392f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266467"
---
# <a name="fatal-error-c1311"></a>致命的なエラー C1311

COFF 形式は、'var' を数値のバイトのアドレスを静的に初期化できません。

アドレスの値がコンパイル時に不明は、型に 4 バイト未満のストレージを持つ変数に静的に割り当てることができません。

このエラーは、それ以外の場合は、コードで発生する可能性が有効な C++ です。

次の例では、C1311 を引き起こす可能性のある 1 つの条件を示します。

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```