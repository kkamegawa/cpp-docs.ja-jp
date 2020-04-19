---
title: NMAKE の致命的なエラー U1045
ms.date: 08/11/2019
f1_keywords:
- U1045
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
ms.openlocfilehash: bdc28bcf02aea791a346a0a74915707fef551b8b
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980541"
---
# <a name="nmake-fatal-error-u1045"></a>NMAKE の致命的なエラー U1045

> 起動に失敗しました:*メッセージ*

NMAKE によって呼び出されたプログラムまたはコマンドが、*メッセージ*の理由により失敗しました。 NMAKE がコンパイラやリンカーなどの別のプログラムを呼び出すと、呼び出しが失敗する可能性があります。 または、呼び出されたプログラムによってエラーが返される場合があります。 このメッセージは、エラーを報告するために使用されます。

この問題を解決するには、まず、エラーの原因を判別します。 NMAKE [/n](../../build/reference/running-nmake.md#nmake-options)オプションによって報告されたコマンドを使用して、環境設定を確認し、コマンドラインで nmake によって実行された操作を繰り返すことができます。
