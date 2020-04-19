---
title: リンカ ツール エラー LNK2027
ms.date: 11/04/2016
f1_keywords:
- LNK2027
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
ms.openlocfilehash: e74912780bab3056ead36ae3705f0910805228e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299011"
---
# <a name="linker-tools-error-lnk2027"></a>リンカ ツール エラー LNK2027

未解決のモジュール参照 ' module'

リンカーに渡されたファイルで指定されているモジュールに依存関係を持つ **/ASSEMBLYMODULE**もリンカーに直接渡されません。

LNK2027 を解決するには、次のいずれかの操作を行います。

- 処理されないリンカーにモジュールの依存関係を含むファイル。

- 使用して、モジュールの指定 **/ASSEMBLYMODULE**します。

- モジュールが安全な .netmodule の場合は、リンカーに直接モジュールを渡します。

詳細については、次を参照してください。 [/ASSEMBLYMODULE (MSIL モジュールのアセンブリへの追加)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)と[リンカー入力としての .netmodule ファイル](../../build/reference/netmodule-files-as-linker-input.md)します。