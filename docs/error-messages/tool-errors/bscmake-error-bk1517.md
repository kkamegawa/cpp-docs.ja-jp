---
title: BSCMAKE エラー BK1517
ms.date: 11/04/2016
f1_keywords:
- BK1517
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
ms.openlocfilehash: 455e028a72cce132c49e0d0d778628ee21bf3a0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380527"
---
# <a name="bscmake-error-bk1517"></a>BSCMAKE エラー BK1517

/Yc および/Yu の両方でコンパイルされた sbrfile のソース ファイル

.Sbr ファイルは、それ自体を参照します。 /Yc でコンパイルした後、再コンパイル/Yu 使用された可能性があります。 /Yc にソース ファイルのコンパイラ オプションをリセットし、選択**リビルド**新しい .sbr ファイルを生成します。 /Yu とソース ファイルを再コンパイルしません。