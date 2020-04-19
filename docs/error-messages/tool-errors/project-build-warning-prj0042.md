---
title: プロジェクト ビルドの警告 PRJ0042
ms.date: 08/27/2018
f1_keywords:
- PRJ0042
helpviewer_keywords:
- PRJ0042
ms.assetid: 682c9999-6f85-409f-b102-00c93243f74f
ms.openlocfilehash: c91e40b6ad56d6201fc7d0ba7c9fbf23e620e8b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297758"
---
# <a name="project-build-warning-prj0042"></a>プロジェクト ビルドの警告 PRJ0042

> 'Outputs' プロパティ ファイルのカスタム ビルド ステップの'*ファイル*' が設定されていません。 カスタム ビルド ステップはスキップされます。

出力が指定されていないために、カスタム ビルド ステップは実行されませんでした。

このエラーを解決するには、次に行ういずれか。

- カスタム ビルド ステップをビルドから除外します。

- 出力を追加します。

- カスタム ビルド ステップのコマンドの内容を削除します。