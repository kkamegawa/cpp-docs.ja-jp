---
title: リンカ ツール エラー LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: 331521c357389c2f7c1aa786969154a2b747ffe5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242826"
---
# <a name="linker-tools-error-lnk1223"></a>リンカ ツール エラー LNK1223

ファイルが無効かまたは壊れています: ファイルに無効な .pdata のコントリビューションが含まれています。

pdata を使用する RISC プラットフォームにおいては、コンパイラによって出力された .pdata セクションのエントリが並べ替えられていない場合に、このエラーが発生します。

この問題を解決するには、なしでコンパイルしてください[/GL (Whole Program Optimization)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md)を有効にします。 また、このエラーは、関数本体が空である場合にも発生することがあります。