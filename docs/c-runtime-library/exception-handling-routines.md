---
title: 例外処理ルーチン
ms.date: 11/04/2016
f1_keywords:
- c.exceptions
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
ms.openlocfilehash: 8def356793906074e6fc4b8d7a139ce1915a5f9b
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749140"
---
# <a name="exception-handling-routines"></a>例外処理ルーチン

C++ 例外処理関数を利用し、プログラム実行中の予想外のイベントから復旧します。

## <a name="exception-handling-functions"></a>例外処理関数

|関数|使用|
|--------------|---------|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Win32 例外 (C 構造化例外) を C++ 型指定例外として処理する|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|**terminate** によって呼び出される独自の終了ルーチンをインストールする|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|**unexpected** によって呼び出される独自の終了関数をインストールする|
|[terminate](../c-runtime-library/reference/terminate-crt.md)|例外がスローされた後、特定の状況下で自動的に呼び出されます。 **terminate** 関数は、**abort** または **set_terminate** で指定した関数を呼び出します|
|[unexpected](../c-runtime-library/reference/unexpected-crt.md)|**terminate** を呼び出すか、または **set_unexpected** を使用して指定した関数を呼び出します。 **unexpected** 関数は現在の Microsoft C++ 例外処理の実装では使用されません|

## <a name="see-also"></a>関連項目

[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
