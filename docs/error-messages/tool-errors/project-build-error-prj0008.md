---
title: プロジェクト ビルド エラー PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 5741b7ef8cb9a7ae53d64874d3531e9271c09e0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359489"
---
# <a name="project-build-error-prj0008"></a>プロジェクト ビルド エラー PRJ0008

ファイル 'file' を削除できませんでした。

**ファイルが別のプロセスによって開かれていないと、書き込み保護されていないことを確認してください。**

Visual C には、すべて既知中間ファイルと出力ファイルのビルド、および指定したワイルドカードと一致するファイルが削除されます再構築中またはクリーン、**クリーン時に削除する拡張機能**プロパティ、[全般構成設定 プロパティ ページ](../../build/reference/general-property-page-project.md)します。

Visual C のファイルを削除することがない場合、このエラーが表示されます。 エラーを解決するには、ファイルとそのディレクトリを書き込み可能のビルドを実行するユーザー。