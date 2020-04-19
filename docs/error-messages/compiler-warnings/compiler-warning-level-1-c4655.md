---
title: コンパイラの警告 (レベル 1) C4655
ms.date: 08/27/2018
f1_keywords:
- C4655
helpviewer_keywords:
- C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
ms.openlocfilehash: aff78dbed217a6d9c5bc2a315ef12a33fe6caf0d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374665"
---
# <a name="compiler-warning-level-1-c4655"></a>コンパイラの警告 (レベル 1) C4655

> '*シンボル*': 変数の型が前回のビルドから新規か異なる方法では、他の場所で定義されています。

## <a name="remarks"></a>Remarks

前回成功したビルド以降に、新しいデータ型が変更または追加されています。 エディット コンティニュは、既存のデータ型への変更をサポートしません。

この警告の後に、 [致命的なエラー C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)が生成されます。 詳細については、「 [サポートされているコード変更](/visualstudio/debugger/supported-code-changes-cpp)」を参照してください。

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>現在のデバッグ セッションを終了せずにこの警告を削除するには

1. データ型をエラーが起こる前の状態に戻します。

2. **[デバッグ]** メニューの **[コード変更を適用]** をクリックします。

### <a name="to-remove-this-warning-without-changing-your-source-code"></a>ソース コードを変更せずにこの警告を削除するには

1. **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。

2. **[ビルド]** メニューの **[ビルド]** をクリックします。