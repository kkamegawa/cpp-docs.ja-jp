---
title: 式エバリュエーター エラー CXX0064
ms.date: 11/04/2016
f1_keywords:
- CXX0064
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
ms.openlocfilehash: 71e4e3e87b33849e6b487b79268ebc9574c2e5a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299479"
---
# <a name="expression-evaluator-error-cxx0064"></a>式エバリュエーター エラー CXX0064

バインドされている仮想メンバー関数にブレークポイントを設定することはできません。

ブレークポイントがなどのオブジェクトへのポインターを介して仮想メンバー関数に設定されました。

```
pClass->vfunc( int );
```

など、クラスを入力して、仮想関数にブレークポイントを設定できます。

```
Class::vfunc( int );
```

このエラーは、can0064 と同じものと同じです。