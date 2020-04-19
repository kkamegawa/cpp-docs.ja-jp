---
title: コンパイラの警告 (レベル 3) C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 56b27596296b87edcc6de406e7b6621d5723815d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402230"
---
# <a name="compiler-warning-level-3-c4192"></a>コンパイラの警告 (レベル 3) C4192

タイプ ライブラリ 'library' のインポート中に 'name' を自動的に除外

A`#import`ライブラリにはアイテムが含まれています*名前*、つまり、Win32 システム ヘッダーでも定義されています。 などのタイプ ライブラリの制限により名**IUnknown** GUID は多くの場合で定義されているタイプ ライブラリでは、システム ヘッダーの定義を複製します。 `#import` これらの項目を検出し、.tlh と .tli ヘッダー ファイルに組み込むことを拒否します。

この動作をオーバーライドするには使用`#import`属性[no_auto_exclude](../../preprocessor/no-auto-exclude.md)と[include()](../../preprocessor/include-parens.md)します。