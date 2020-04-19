---
title: コンパイラの警告 (レベル 1) C4656
ms.date: 11/04/2016
f1_keywords:
- C4656
helpviewer_keywords:
- C4656
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
ms.openlocfilehash: 4285ce20f6131c2503304ed1bdb1bde02b2efcec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375250"
---
# <a name="compiler-warning-level-1-c4656"></a>コンパイラの警告 (レベル 1) C4656

'symbol': データ型は、新しいがまたは前回のビルド以降に変更されたか、異なる方法では、他の場所で定義されています。

前回成功したビルド以降に、データ型が追加されたか既存のデータ型が変更されました。これは、今までソース コードに含まれていなかったデータ型です。 エディット コンティニュは、既存のデータ型への変更をサポートしません。

この警告の後に必ず [致命的なエラー C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)が生成されます。 詳細については、「 [サポートされているコード変更](/visualstudio/debugger/supported-code-changes-cpp)」を参照してください。

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>現在のデバッグ セッションを終了せずにこの警告を削除するには

1. データ型をエラーが起こる前の状態に戻します。

1. **[デバッグ]** メニューの **[コード変更を適用]** をクリックします。

### <a name="to-remove-this-error-without-changing-your-source-code"></a>ソース コードを変更せずにこのエラーを削除するには

1. **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。

1. **[ビルド]** メニューの **[ビルド]** をクリックします。