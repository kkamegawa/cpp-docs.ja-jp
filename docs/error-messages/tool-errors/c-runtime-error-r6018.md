---
title: C ランタイム エラー R6018
ms.date: 11/04/2016
f1_keywords:
- R6018
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
ms.openlocfilehash: b36e2184e5be131645fb4dd58a361fdb9a31da63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214221"
---
# <a name="c-runtime-error-r6018"></a>C ランタイム エラー R6018

ヒープの予期しないエラー

> [!NOTE]
> アプリの実行中にこのエラー メッセージが発生した場合、アプリがシャット ダウン内部の問題があるためです。 このエラーは、いくつかの理由がありますが、多くの場合、アプリのコードの欠陥、原因が。
>
> このエラーを解決するには、次の手順を試してみます。
>
> - 使用して、**アプリおよび機能**または**プログラムと機能**ページで、**コントロール パネルの** を修復またはプログラムを再インストールします。
> - 確認**Windows Update**で、**コントロール パネルの** ソフトウェアの更新。
> - アプリの更新バージョンを確認します。 問題が解決しない場合は、アプリのベンダーにお問い合わせください。

**プログラマのための情報**

プログラムでは、メモリ管理操作を実行中に予期しないエラーが発生しました。

このエラーは、通常、プログラムが実行時のヒープのデータを誤って変更する場合に発生します。 ただし、それも可能性がありますランタイムまたはオペレーティング システムのコードで内部エラー。

この問題を解決するには、コードのヒープ破損のバグを確認します。 詳細と例については、次を参照してください。 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)します。 次に、アプリの展開に関する最新の再頒布可能パッケージを使用していることを確認します。 詳しくは、次を参照してください。 [Deployment in Visual c](../../windows/deployment-in-visual-cpp.md)します。