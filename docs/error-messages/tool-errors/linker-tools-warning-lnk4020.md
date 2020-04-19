---
title: リンカー ツールの警告 LNK4020
ms.date: 05/29/2018
f1_keywords:
- LNK4020
helpviewer_keywords:
- LNK4020
ms.openlocfilehash: 7810fd9a97a8f6e22ad362819a024358a9f4b07c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298582"
---
# <a name="linker-tools-warning-lnk4020"></a>リンカー ツールの警告 LNK4020

> 型のレコードに '*filename*' が破損しています一部のシンボルよぶ型をデバッガーからはアクセスできない可能性があります。

PDB ファイル*filename*が破損している型のレコード。

この問題は、その他のビルドの問題; にセカンダリが多くの場合、その他のエラーと警告で処理を最初の報告されるビルドの問題である場合を除き、最初。 これは、最初の報告された問題である場合は、ビルド ディレクトリを消去し、プロジェクトをリビルドする必要があります。 並列ビルド プロセスを使用する場合は、ビルドをシリアル化するときにエラーが発生するかどうかを参照してください。