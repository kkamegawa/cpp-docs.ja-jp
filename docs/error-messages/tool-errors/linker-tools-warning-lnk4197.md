---
title: リンカー ツールの警告 LNK4197
ms.date: 09/05/2018
f1_keywords:
- LNK4197
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
ms.openlocfilehash: 0abad1b98ff4782f077312752603ec17fd611c12
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390361"
---
# <a name="linker-tools-warning-lnk4197"></a>リンカー ツールの警告 LNK4197

> エクスポート '*exportname*' 複数回; 最初の仕様を使用して指定されました。

エクスポートが複数の指定とさまざまな方法です。 リンカーは、最初の仕様を使用し、残りの部分を無視します。

C ランタイム ライブラリを再構築する場合は、このメッセージを無視できます。

エクスポートが複数回にまったく同じ方法を指定する場合、リンカーは警告を発行しません。

たとえば、.def ファイルの次の内容では、この警告が発生します。

```
EXPORTS
   functioname      NONAME
   functioname      @10
```

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. 同じエクスポートが指定されたコマンドラインの両方 (エクスポートによって:) および .def ファイル。

2. 同じエクスポートは、異なる属性を持つ .def ファイルに 2 回表示されます。