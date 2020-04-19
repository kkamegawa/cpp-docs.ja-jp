---
title: プロジェクト ビルド エラー PRJ0009
ms.date: 11/04/2016
f1_keywords:
- PRJ0009
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
ms.openlocfilehash: 963b7c861f9e8ee7105ebdc23afff08c4be46465
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359502"
---
# <a name="project-build-error-prj0009"></a>プロジェクト ビルド エラー PRJ0009

ビルド ログを書き込むのために開けませんでした。

**ファイルが別のプロセスによって開かれていないと、書き込み保護されていないことを確認してください。**

設定した後、**ビルドのログ**プロパティを**はい**ビルドまたはリビルドを実行する Visual C なしで排他モードでビルド ログを開くことができません。

検査、**ビルドのログ**設定を開いて、**オプション** ダイアログ ボックス (上、**ツール** メニューのをクリックして**オプション**コマンド) し、選択**VC++ ビルド**で、**プロジェクト**フォルダー。 ビルド ファイルでは、名前は buildlog.htm され、中間ディレクトリ $(IntDir) に書き込まれます。

このエラーの考えられる理由:

- Visual C の 2 つのプロセスを実行して同時に同じ構成の両方で同じプロジェクトをビルドしようとしています。

- ビルド ログ ファイルは、ファイルをロックするプロセスで開かれます。

- ユーザーには、ファイルを作成するためのアクセス許可がありません。

- 現在のユーザーには、BuildLog.htm ファイルに書き込みアクセス権がありません。