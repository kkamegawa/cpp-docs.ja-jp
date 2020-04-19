---
title: プロジェクト ビルド エラー PRJ0006
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: d62c774411fda80a3e94044b3272567177328ff5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359658"
---
# <a name="project-build-error-prj0006"></a>プロジェクト ビルド エラー PRJ0006

一時ファイル 'file' を開けませんでした。 ファイルが存在し、こと、ディレクトリが書き込み禁止してください。

Visual C は、ビルド プロセス中に一時ファイルを作成できませんでした。 理由が考えられます。

- 一時ディレクトリがありません。

- 読み取り専用の一時ディレクトリ。

- ディスク領域。

- $ (Intdir) フォルダーが読み取り専用か読み取り専用である一時ファイルが含まれています。

このエラーは、次のエラー PRJ0007 も発生します。出力ディレクトリ 'directory' を作成できませんでした。 エラー PRJ0007 は、$ (intdir) ディレクトリを作成できませんでした、一時的にファイルの作成も失敗することを意味します。

指定するには、一時ファイルが作成されます。

- 応答ファイルです。

- カスタム ビルド ステップ。

- ビルド イベントです。