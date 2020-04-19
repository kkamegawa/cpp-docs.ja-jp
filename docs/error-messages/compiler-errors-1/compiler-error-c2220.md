---
title: コンパイラ エラー C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: 3ff730c6fea7d2c57c4ec3054fc627cdc6227e2d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311749"
---
# <a name="compiler-error-c2220"></a>コンパイラ エラー C2220

warning treated as error - no object file generated

[/WX](../../build/reference/compiler-option-warning-level.md)すべての警告をエラーとして扱うようにコンパイラに指示します。 エラーが発生したため、オブジェクトまたは実行可能ファイルは生成されませんでした。

このエラー場合にのみ、 **/WX**フラグが設定され、コンパイル時に警告が発生します。 このエラーを解決するには、プロジェクトのすべての警告を除去する必要があります。

### <a name="to-fix-use-one-of-the-following-techniques"></a>解決するには、次のいずれかの手法を使用します。

- プロジェクトの警告の原因となった問題を解決します。

- 下の警告レベルのコンパイルなどを使用して、 **/W3**の代わりに **/W4**します。

- 使用して、[警告](../../preprocessor/warning.md)プラグマを無効にするか、または特定の警告を抑制します。

- 使用しない **/WX**をコンパイルします。