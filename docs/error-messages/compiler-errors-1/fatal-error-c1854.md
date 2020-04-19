---
title: 致命的なエラー C1854
ms.date: 11/04/2016
f1_keywords:
- C1854
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
ms.openlocfilehash: 83eb5e01eac377b8f19a0e94dc1518e3ed557c3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165643"
---
# <a name="fatal-error-c1854"></a>致命的なエラー C1854

> オブジェクト ファイルでプリコンパイル済みヘッダーの作成中に情報を上書きすることはできません: '*filename*'

指定した、 [/Yu (プリコンパイル済みヘッダー ファイルの使用)](../../build/reference/yu-use-precompiled-header-file.md)オプションを指定した後、 [/Yc (プリコンパイル済みヘッダー ファイルの作成)](../../build/reference/yc-create-precompiled-header-file.md)同じファイル オプションを指定します。

この問題を解決するを使用してコンパイルするプロジェクトで一般に、1 つのファイルを設定、 **/Yc**オプション、およびその他のすべてのファイルを使用してコンパイルする設定、 **/Yu**オプション。 詳細については、使用するときの **/Yc**オプション、および Visual Studio IDE で設定を参照してください方法[/Yc (プリコンパイル済みヘッダー ファイルの作成)](../../build/reference/yc-create-precompiled-header-file.md)。 プリコンパイル済みヘッダーの使用の詳細については、次を参照してください。[プリコンパイル済みヘッダー ファイルの作成](../../build/creating-precompiled-header-files.md)です。
