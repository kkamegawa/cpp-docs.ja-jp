---
title: コンパイラの警告 (レベル 1) C4951
ms.date: 08/27/2018
f1_keywords:
- C4951
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
ms.openlocfilehash: 73e048aeaa044c35e09539b07d51398829a0fdfd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408059"
---
# <a name="compiler-warning-level-1-c4951"></a>コンパイラの警告 (レベル 1) C4951

> '*関数*' からプロファイル データが収集された関数のプロファイル データは使用されませんが編集されました

[/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)への入力モジュールの関数が編集されたため、プロファイル データが無効になりました。 入力モジュールは、 **/LTCG:PGINSTRUMENT** の後に再コンパイルされ、*/LTCG:PGINSTRUMENT*の操作時にモジュールに含まれていたものとは異なる制御フローを使用した関数 ( **function** ) が含まれています。

これは、情報提供の警告です。 この警告を解決するには、 **/LTCG:PGINSTRUMENT**を実行してすべてのテストを再実行し、 **/LTCG:PGOPTIMIZE**を実行します。

**/LTCG:PGOPTIMIZE** が使用されていた場合、この警告はエラーに置き換わることがあります。