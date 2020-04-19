---
title: リンカー ツールの警告 LNK4102
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: 0f9c8649988dd3056e98730ac4b02022a8c9dd51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327263"
---
# <a name="linker-tools-warning-lnk4102"></a>リンカー ツールの警告 LNK4102

削除するデストラクター 'name';イメージは正しく動作しない可能性があります。

プログラムが削除するデストラクターをエクスポートしようとしました。 Delete は、DLL 境界を越えて、プロセスが所有していないメモリを解放するように発生します。 .Def ファイルで指定されたシンボルが表示されていないことと、シンボルがの引数として表示されていないことを確認、 **/インポート**または **/export**リンカー コマンドラインのオプション。

C ランタイム ライブラリを再構築する場合は、このメッセージを無視できます。