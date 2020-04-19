---
title: リンカー ツールの警告 LNK4099
ms.date: 11/04/2016
f1_keywords:
- LNK4099
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
ms.openlocfilehash: dcf4d44c3a0b5b10035af763040c2912afc8c6f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310891"
---
# <a name="linker-tools-warning-lnk4099"></a>リンカー ツールの警告 LNK4099

Pdb ファイル 'filename' の 'オブジェクト/ライブラリ' または 'path'; に見つかりませんデバッグ情報オブジェクトをリンク

リンカーは、.pdb ファイルが見つかりませんでした。 格納されているディレクトリにコピー`object/library`します。

オブジェクト ファイルに関連付けられた .pdb ファイルの名前を検索するには。

1. オブジェクト ファイルをライブラリから抽出[lib](../../build/reference/lib-reference.md) **/extract:**`objectname`**.obj** `xyz` **.lib**します。

1. .Pdb ファイルへのパスを確認してください。 **dumpbin/section:.debug$ T/rawdata** `objectname` **.obj**します。

コンパイルすることも[/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)pdb ファイルは、使用、または削除する必要があるため、 [/debug](../../build/reference/debug-generate-debug-info.md)リンカー オプションは、リンク オブジェクトの .pdb ファイルがあるない場合。