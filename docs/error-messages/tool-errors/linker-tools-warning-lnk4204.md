---
title: リンカー ツールの警告 LNK4204
ms.date: 11/04/2016
f1_keywords:
- LNK4204
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
ms.openlocfilehash: 790b0fa25bbf41c38b843e1a2ea757fdc0d10b9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395106"
---
# <a name="linker-tools-warning-lnk4204"></a>リンカー ツールの警告 LNK4204

'filename' が参照するモジュールのデバッグ情報がありません。デバッグ情報オブジェクトをリンク

.Pdb ファイルには、エラーのある署名があります。 リンカーでは、引き続きデバッグ情報なしオブジェクトをリンクします。 オブジェクト ファイルを使用して、再コンパイルすることも、 [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)オプション。

LNK4204 は、存在しなくなったファイルを参照してください、ライブラリ内のオブジェクトのいくつかの場合に発生することができます。 これは、現象は、ソリューションを再構築するときなどです。オブジェクト ファイルは削除され、コンパイル エラーのため再構築しない可能性があります。 使用してこの例では、いずれかのコンパイル **/Z7**、または **/Fd**、1 つのファイルごとにライブラリを (既定の .pdb ファイル名ではありません) を参照するオブジェクトを更新します。  詳細については、「[/Fd (プログラム データベース ファイル名)](../../build/reference/fd-program-database-file-name.md)」を参照してください。  ソース管理システムで更新されるたびに、ライブラリと .pdb ファイルが保存されていることを確認します。