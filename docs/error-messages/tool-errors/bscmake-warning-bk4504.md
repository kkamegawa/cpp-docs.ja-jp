---
title: BSCMAKE の警告 BK4504
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 7ffcb7c2e6ae512006ccd29c87b05c53fdfcaef5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279302"
---
# <a name="bscmake-warning-bk4504"></a>BSCMAKE の警告 BK4504

ファイルには、参照が多すぎます; が含まれています。このソースからさらに参照を無視します。

.Cpp ファイルには、64,000 を超えるシンボル参照が含まれています。 BSCMAKE では、ファイルで 64,000 の参照が発生したとき、に、それ以上のすべての参照を無視します。

問題を修正する 2 つのファイルに分割またはのいずれかがより少ない 64,000 以上のファイルのシンボル参照、またはを使用して、`#pragma component(browser)`プリプロセッサ ディレクティブの特定の参照用に生成されたシンボルを制限します。 詳細については、次を参照してください。[コンポーネント](../../preprocessor/component.md)します。