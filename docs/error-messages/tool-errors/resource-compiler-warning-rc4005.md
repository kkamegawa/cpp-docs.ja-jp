---
title: リソース コンパイラの警告 RC4005
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: 571c4ac285e9477b017dbc21cf9ff733539759d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346185"
---
# <a name="resource-compiler-warning-rc4005"></a>リソース コンパイラの警告 RC4005

'identifier': 再定義はマクロ

識別子は、2 回定義されます。 コンパイラは、2 つ目のマクロ定義を使用します。

この警告は、コマンドラインで、コードで、マクロの定義によって発生すること、`#define`ディレクティブ。 それも可能性がありますインクルード ファイルからインポートされたマクロで。

警告を排除するために、定義の 1 つを削除またはのいずれかを使用して、`#undef`ディレクティブを 2 番目の定義。