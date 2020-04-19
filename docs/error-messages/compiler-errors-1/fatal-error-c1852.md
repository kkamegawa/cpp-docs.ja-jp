---
title: 致命的なエラー C1852
ms.date: 11/04/2016
f1_keywords:
- C1852
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
ms.openlocfilehash: 895c2fc988c9566f9e50b1ac1a18eb4dc1c6661a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165737"
---
# <a name="fatal-error-c1852"></a>致命的なエラー C1852

'filename' は有効なプリコンパイル済みヘッダー ファイルではありません

ファイルはプリコンパイル済みヘッダーではありません。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. **/Yu** または **#pragma hdrstop**で指定された無効なファイル。

1. 特に指定がない場合、コンパイラはファイル拡張子を .pch と想定します。