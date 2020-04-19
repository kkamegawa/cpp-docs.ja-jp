---
title: NMAKE の致命的なエラー U1059
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 3c148bf2feb7ba12686e00b29f5bf90cb9f2f2d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367292"
---
# <a name="nmake-fatal-error-u1059"></a>NMAKE の致命的なエラー U1059

> 構文エラー: '}' に依存します。

依存ファイルの検索パスが正しく指定されていません。 パスまたは右中かっこに空白が存在していた (**}**) を省略した場合します。

依存ファイルのディレクトリの指定の構文は、

> **{** *ディレクトリ* **} 依存**

場所*ディレクトリ*1 つまたは複数のパスをセミコロンで区切って指定それぞれを指定します (**;**)。 スペースは許可されません。

検索パスの一部またはすべては、マクロに置き換え場合、は、マクロ展開中にスペースが存在しないことを確認してください。