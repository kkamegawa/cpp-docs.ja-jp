---
title: 数値演算エラー M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: d60e9b6284c79828fda1f7af542fcf197f189ad0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393273"
---
# <a name="math-error-m6108"></a>数値演算エラー M6108

平方根

平方根演算のオペランドが負の値。

終了コード 136 でプログラムを終了します。

> [!NOTE]
>  `sqrt` C ランタイム ライブラリと FORTRAN の組み込み関数の関数**SQRT**このエラーは生成されません。 C`sqrt`関数は、操作を実行する前に、引数をチェックし、オペランドが負の場合は、エラー値を返します。 FORTRAN **SQRT**関数には、ドメイン エラーが生成されます。 [M6201](../../error-messages/tool-errors/math-error-m6201.md)このエラーの代わりにします。