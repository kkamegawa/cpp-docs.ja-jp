---
title: 致命的なエラー C1902
ms.date: 11/04/2016
f1_keywords:
- C1902
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
ms.openlocfilehash: c425430a6d08ae8a97c4dcd0f5764f44dee43e5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165867"
---
# <a name="fatal-error-c1902"></a>致命的なエラー C1902

プログラム データベース マネージャーが一致しません。インストールを確認してください。

プログラム データベース ファイル (.pdb) は、新しいバージョンの mspdb を使用して作成された*XXX*.dll、システムで、コンパイラが検出されたものです。 このエラーは mspdbsrv.exe または mspdbcore.dll が見つからないか、mspdb は異なるバージョンがあることには、通常を示します*XXX*.dll です。 (、 *XXX* 、mspdb 内のプレース ホルダー*XXX*製品リリースごとに .dll ファイル名の変更。 たとえば、Visual Studio 2015 で、ファイル名は mspdb140.dll。)

Mspdbsrv.exe、mspdbcore.dll、mspdb の一致するバージョンを確認します。*XXX*.dll は、システムにインストールされます。 バージョンが一致しないが、ターゲット プラットフォームのコンパイラとリンク ツールを含むディレクトリにコピーされていないことを確認します。 たとえば、する可能性がありますファイルをコピー、設定がない場合、コマンド プロンプトから、コンパイラまたはリンク ツールを起動できるように、**パス**環境変数それに応じて。