---
title: リンカ ツール エラー LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: c3b1117b31db4759b385943323a581da7a58f0c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160446"
---
# <a name="linker-tools-error-lnk1302"></a>リンカ ツール エラー LNK1302

安全な .netmodule は; をリンクのみをサポートします.netmodule のファイルをリンクできません。

.Netmodule (でコンパイルされた **/LN**) を呼び出す MSIL リンク ユーザーの試行時に、リンカーに渡されました。  C++ モジュールは、MSIL にコンパイルする場合のリンクの有効な **/clr:safe**します。

このエラーを修正するとコンパイル **/clr:safe** MSIL がリンクを有効にまたはパス、 **/clr**または **/clr: 純粋な**モジュールではなく、リンカーを .obj ファイル。

詳細については、次のトピックを参照してください。

- [/LN (MSIL モジュールの作成)](../../build/reference/ln-create-msil-module.md)

- [.netmodule ファイル (リンカー入力)](../../build/reference/netmodule-files-as-linker-input.md)