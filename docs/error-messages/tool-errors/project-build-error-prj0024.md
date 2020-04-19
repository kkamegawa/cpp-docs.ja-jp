---
title: プロジェクト ビルド エラー PRJ0024
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: 645b898bdffcc6d7b397c25eb3c41cea25cb361f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384104"
---
# <a name="project-build-error-prj0024"></a>プロジェクト ビルド エラー PRJ0024

> Unicode のパス '*パス*' ユーザーの ANSI コード ページに変換できませんでした。

*パス*パス文字列の元の Unicode バージョンです。 場合にこのエラーは発生が Unicode パスを直接に変換できない ANSI の現在のシステム コード ページ。

場合は、コンピューターではないにコード ページを使用してシステムで開発されたプロジェクトに取り組んで、このエラーが発生する可能性があります。

このエラーの解決は、ANSI テキストを使用して、または、コード ページをコンピューターにインストールし、システムの既定値として設定するパスを更新するには。