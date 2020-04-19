---
title: リソース コンパイラ エラー RC2001
ms.date: 11/04/2016
f1_keywords:
- RC2001
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
ms.openlocfilehash: f4755e04a744d94636b4b37aaf727e0d733008ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346692"
---
# <a name="resource-compiler-error-rc2001"></a>リソース コンパイラ エラー RC2001

定数の新しい行

文字列定数は続行されたことがなく行目では、円記号 (**\\**) または二重引用符をオープン/クローズ (**"**)。

ソース ファイル内の 2 つの行にある文字列定数を解除するには、次のいずれかの操作を行います。

- 行連結文字の円記号で最初の行を終了します。

- 二重引用符では、最初の行の文字列を閉じて、もう 1 つの引用符、次の行の文字列を開きます。

\N、文字列定数に改行文字を埋め込むためのエスケープ シーケンスでは、最初の行を終了するのに十分ではありません。