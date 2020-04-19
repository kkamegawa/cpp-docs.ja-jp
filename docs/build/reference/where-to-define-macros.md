---
title: マクロを定義する場所
ms.date: 11/04/2016
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
ms.openlocfilehash: dc03644adea4619b3eabe33c481d71f704a9f410
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316367"
---
# <a name="where-to-define-macros"></a>マクロを定義する場所

コマンドライン、コマンド ファイル、メイクファイルでまたは tools.ini マクロを定義します。

メイクファイルまたは Tools.ini ファイルでは、各マクロ定義が別々 の行に表示する必要があり、スペースまたはタブで始めることはできません。スペースや等号 (=) の周囲のタブは無視されます。 すべて[文字の文字列](defining-an-nmake-macro.md)リテラルを囲む引用符と埋め込み型スペースなどです。

コマンド ファイルまたはコマンドラインで引数を区切るスペースとタブと、等号 (=) で囲むことはできません。 場合`string`スペースまたはタブが埋め込まれて、文字列自体または全体のマクロのいずれかを二重引用符で囲みます ("")。

## <a name="see-also"></a>関連項目

[NMAKE マクロの定義](defining-an-nmake-macro.md)
