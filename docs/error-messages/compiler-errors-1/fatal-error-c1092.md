---
title: 致命的なエラー C1092
ms.date: 11/04/2016
f1_keywords:
- C1092
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
ms.openlocfilehash: 3268e5b124be40313bdc97b4c95d935ddd4f9160
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208547"
---
# <a name="fatal-error-c1092"></a>致命的なエラー C1092

エディット コンティニュはデータ型への変更をサポートしません。ビルドが必要です。

変更または前回の成功したビルドからデータ型を追加します。

- エディット コンティニュは、クラス、構造体、または列挙型の定義を含む、既存のデータ型に変更をサポートしていません。 デバッグを停止し、アプリケーションをビルドする必要があります。

- エディット コンティニュが vc などのプログラム データベース ファイルの場合、新しいデータ型の追加をサポートしていない*x*0. pdb (場所*x*使用中の Visual C のメジャー バージョン) は読み取り専用です。 データ型を追加するには、コンパイラが、書き込みモードで .pdb ファイルを開く必要があります。

### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>現在のデバッグ セッションを終了せずにこのエラーを削除するには

1. データ型をエラーが起こる前の状態に戻します。

1. **[デバッグ]** メニューの **[コード変更を適用]** をクリックします。

### <a name="to-remove-this-error-without-changing-your-source-code"></a>ソース コードを変更せずにこのエラーを削除するには

1. **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。

1. **[ビルド]** メニューの **[ビルド]** をクリックします。

詳細については、「 [サポートされているコード変更](/visualstudio/debugger/supported-code-changes-cpp)」を参照してください。