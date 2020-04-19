---
title: リソース コンパイラ エラー RC2144
ms.date: 11/04/2016
f1_keywords:
- RC2144
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
ms.openlocfilehash: deabd639e04d5b78b398cda9245e9726e2124740
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173471"
---
# <a name="resource-compiler-error-rc2144"></a>リソース コンパイラ エラー RC2144

主言語 ID が数字ではありません。

主言語 ID は 16 進数の言語 ID にする必要があります。 有効な言語 ID の一覧については、「 [ランタイム ライブラリ リファレンス](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) 」の「 *言語および国/地域識別文字列* 」を参照してください。

このエラーは、ツールを使用して、.RC ファイルにリソースを追加してから削除した場合にも発生することがあります。 この問題を解決するには、.RC ファイルをテキスト エディターで開き、使用されていないすべてのリソースを手動でクリーンアップします。