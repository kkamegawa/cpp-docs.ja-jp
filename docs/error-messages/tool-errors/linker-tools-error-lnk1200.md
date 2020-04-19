---
title: リンカ ツール エラー LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: c99b25a83836f1ee0bc6ba622e42ea382c377172
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62213551"
---
# <a name="linker-tools-error-lnk1200"></a>リンカ ツール エラー LNK1200

プログラム データベース 'filename' を読み取り中にエラー

プログラム データベース (PDB) を読み取ることができませんでした。

このエラーは、ファイルの破損によって発生することができます。

場合`filename`pdb ファイルは、オブジェクトのファイルで、ファイルを使用してオブジェクトを再コンパイル[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)します。

場合`filename`PDB および再リンクの削除、メイン出力ファイルの PDB であり、インクリメンタル リンク中にこのエラーが発生しました。