---
title: 式エバリュエーター エラー CXX0019
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 266e97f28cf0f27cb87e9743399c66aba87c0e8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397108"
---
# <a name="expression-evaluator-error-cxx0019"></a>式エバリュエーター エラー CXX0019

無効な型キャスト

C の式エバリュエーターでは、型キャストを実行できません。

このエラーは、can0019 と同じものと同じです。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. 指定した型が不明です。

1. ポインター型のレベルが多すぎますが発生しました。 たとえば、型キャスト

    ```
    (char **)h_message
    ```

   C の式エバリュエーターによって評価ことはできません。