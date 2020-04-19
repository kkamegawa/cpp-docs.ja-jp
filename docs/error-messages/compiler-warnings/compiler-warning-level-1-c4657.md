---
title: コンパイラの警告 (レベル 1) C4657
ms.date: 11/04/2016
f1_keywords:
- C4657
helpviewer_keywords:
- C4657
ms.assetid: eb750050-cea6-4ead-b80c-d5dcd4971cfc
ms.openlocfilehash: 92415d1d17c3342dbb721aa850f37f4dfabd1406
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375692"
---
# <a name="compiler-warning-level-1-c4657"></a>コンパイラの警告 (レベル 1) C4657

前回のビルド以降新規に追加されたデータ型が数式に含まれています

前回成功したビルド以降に、データ型が追加されたか既存のデータ型が変更されました。これは、今までソース コードに含まれていなかったデータ型です。 エディット コンティニュは、既存のデータ型への変更をサポートしません。

この警告の後に必ず [致命的なエラー C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)が生成されます。 詳細については、「 [サポートされているコード変更](/visualstudio/debugger/supported-code-changes-cpp)」を参照してください。

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>現在のデバッグ セッションを終了せずにこの警告を削除するには

1. データ型をエラーが起こる前の状態に戻します。

1. **[デバッグ]** メニューの **[コード変更を適用]** をクリックします。

### <a name="to-remove-this-error-without-changing-your-source-code"></a>ソース コードを変更せずにこのエラーを削除するには

1. **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。

1. **[ビルド]** メニューの **[ビルド]** をクリックします。