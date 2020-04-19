---
title: リンカー ツールの警告 LNK4092
ms.date: 11/04/2016
f1_keywords:
- LNK4092
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
ms.openlocfilehash: 0b18002135d225a90f7e45adc2ff57a64c0a79f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279321"
---
# <a name="linker-tools-warning-lnk4092"></a>リンカー ツールの警告 LNK4092

共有書き込みセクション 'section'; の再配置が含まれていますイメージは正しく動作しない可能性があります。

リンカーは、共通のセクションを警告する可能性がある重大な問題がある場合、この警告を出力します。

複数のプロセス間のデータを共有する方法の 1 つは、セクションに「共有」のマークを付けます ただし、共有セクションをマークすると問題が発生することができます。 たとえば、共有データ セクションでは、このような宣言を含む DLL があります。

```
int var = 1;
int *pvar = &var;
```

リンカーを解決できない`pvar`その値が、DLL がメモリに読み込まれている依存しているためため再配置レコードに入れ、DLL。 メモリのアドレスに DLL が読み込まれるときに`var`を解決できると`pvar`割り当てられます。 別のプロセスは同じ DLL を読み込みますが、同時に読み込むことができませんがある場合の対処のアドレスの再配置`var`2 番目のプロセスと最初のプロセスのアドレス空間が間違ったアドレスを指しますが更新されます。