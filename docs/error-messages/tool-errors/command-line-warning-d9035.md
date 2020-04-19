---
title: コマンド ラインの警告 D9035
ms.date: 12/10/2018
f1_keywords:
- D9035
helpviewer_keywords:
- D9035
ms.assetid: 6254f933-e37a-45ba-b860-1a870d1bc8e8
ms.openlocfilehash: 9c0a159dcf193b4ad016069bafd86c557e9e1281
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62213771"
---
# <a name="command-line-warning-d9035"></a>コマンド ラインの警告 D9035

> オプション '*オプション*' は非推奨し、将来のリリースで削除される予定

## <a name="remarks"></a>Remarks

コンパイラの将来のリリースで削除されるコンパイラ オプションを指定したとします。 場合の推奨される代替*オプション*、この警告は、後で警告[D9036](../../error-messages/tool-errors/command-line-warning-d9036.md)します。

指定したオプションは引き続き機能しますが、今すぐビルド構成を更新する必要があります。 その結果、プロジェクトは、コンパイラのアップグレード時に作成を続行する可能性が高くなります。

## <a name="see-also"></a>関連項目

[非推奨と削除されたコンパイラ オプション](../../build/reference/compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options)<br/>
[コマンド ラインの警告 D9036](command-line-warning-d9036.md)