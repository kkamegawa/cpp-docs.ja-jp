---
title: BSCMAKE エラー BK1513
ms.date: 11/04/2016
f1_keywords:
- BK1513
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
ms.openlocfilehash: c02e9b47b3d32e4d21914188b96913d6dff03127
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279303"
---
# <a name="bscmake-error-bk1513"></a>BSCMAKE エラー BK1513

インクリメンタルでないビルドにはすべての .SBR ファイルが必要です。

1 つ以上の .sbr ファイルが切り捨てられたため、BSCMAKE では、新しいブラウザー情報 (.bsc) ファイルをビルドできません。 切り捨てられた .sbr ファイルの名前を検索するには、読み取り、 [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md)このエラーを警告します。

BSCMAKE では .bsc ファイルを切り捨てられた .sbr ファイルで更新できますが、新しいものをビルドすることはできません。 BSCMAKE では、次の理由で新しい .bsc ファイルをビルドする可能性があります。

- .bsc ファイルが欠落しています。

- .bsc ファイルに指定されたファイル名が間違っています。

- .bsc ファイルが破損しています。

この問題を解決するには、切り捨てられた .sbr ファイルを削除して再ビルドするか、または、ソリューションをクリーンして再ビルドします。 (IDE では、次のように選択します**ビルド**、**ソリューションのクリーン**を選び、**ビルド**、**ソリューションのリビルド**。)。