---
title: リンカ ツール エラー LNK2004
ms.date: 11/04/2016
f1_keywords:
- LNK2004
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
ms.openlocfilehash: 8088494106aa702fda0497fa431e48267167a185
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160420"
---
# <a name="linker-tools-error-lnk2004"></a>リンカ ツール エラー LNK2004

gp 相対 fixup のオーバーフローを 'ターゲット';short セクション 'section' は大きすぎる、または範囲外です。

セクションが大きすぎます。

このエラーを解決するには、#pragma セクション (".sectionname"を読み取り、書き込み、時間の長い) を使用して、長いセクションでデータを明示的に設定しを使用していずれかの短いセクションのサイズを小さく`__declspec(allocate(".sectionname"))`データ定義と宣言します。  例えば以下のようにします。

```
#pragma section(".data$mylong", read, write, long)
__declspec(allocate(".data$mylong"))
char    rg0[1] = { 1 };
char    rg1[2] = { 1 };
char    rg2[4] = { 1 };
char    rg3[8] = { 1 };
char    rg4[16] = { 1 };
char    rg5[32] = { 1 };
```

長い形式のデータ セクションでは、コンパイラが割り当てるは 8 バイトを超えるデータのコレクションとなる、独自の構造に論理的にグループ化したデータを移動することもできます。  例えば以下のようにします。

```
// from this...
int     w1  = 23;
int     w2 = 46;
int     w3 = 23*3;
int     w4 = 23*4;

// to this...
struct X {
    int     w1;
    int     w2;
    int     w3;
    int     w4;
} x  = { 23, 23*2, 23*3, 23*4 };
```

このエラーは致命的なエラー続けて`LNK1165`します。