---
title: 致命的なエラー C1352
ms.date: 11/04/2016
f1_keywords:
- C1352
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
ms.openlocfilehash: fbba87cea05d666d6dc3a385ca1fe52e143fdb5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329726"
---
# <a name="fatal-error-c1352"></a>致命的なエラー C1352

関数 'function' (元モジュール 'file') の無効な、または壊れた MSIL です。

.netmodule がコンパイラに渡されましたが、コンパイラでファイルの破損が検出されました。  調査するために .netmodule の作成者に問い合わせてください。

コンパイラは、.netmodule ファイルのすべての種類の破損をチェックしません。  ただし、return ステートメントを含む関数内のすべてのコントロール パスのすべての種類の破損をチェックします。

詳細については、「 [リンカー入力としての .netmodule ファイル](../../build/reference/netmodule-files-as-linker-input.md)」を参照してください。