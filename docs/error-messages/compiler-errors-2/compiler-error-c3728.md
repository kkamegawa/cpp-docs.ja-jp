---
title: コンパイラ エラー C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 68aa23843b0470f15f409b6f3b58624f979ccfae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328108"
---
# <a name="compiler-error-c3728"></a>コンパイラ エラー C3728

'event': イベントに raise メソッドがありません

C# で定義されていたクラスの外部から発生するイベントが許可されないに付属していたようにメタデータが、言語で作成、 [#using](../../preprocessor/hash-using-directive-cpp.md)ディレクティブ、およびしようとする CLR プログラミングを使用して、Visual C プログラムイベントが発生します。

C# などの言語で開発されたプログラムでイベントを発生させるには、イベントを含むクラスにも、イベントを発生させるパブリック メソッドを定義する必要があります。