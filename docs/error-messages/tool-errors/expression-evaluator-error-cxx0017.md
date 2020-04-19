---
title: 式エバリュエーター エラー CXX0017
ms.date: 11/04/2016
f1_keywords:
- CXX0017
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
ms.openlocfilehash: bbf16ae9a503a8525edb42d6bf1fc4336c3f5267
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397134"
---
# <a name="expression-evaluator-error-cxx0017"></a>式エバリュエーター エラー CXX0017

シンボルが見つかりません

式で指定されたシンボルが見つかりませんでした。

このエラーの考えられる原因の 1 つは、シンボル名の大文字と小文字が一致しません。 C および C++ 言語の区別があるため、ソースで定義されている大文字小文字の区別のシンボル名を与える必要があります。

このエラーは、デバッグ中に、変数を監視するために変数を型キャストしようとするときに発生することができます。 `typedef`型の新しい名前を宣言しますが、新しい型を定義しません。 型キャスト、デバッガーで試行すると、定義された型の名前が必要です。

このエラーは、can0017 と同じものと同じです。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>以下の可能性がある解決策を使って修正するには

1. シンボルが既に位置が使用中のプログラムで宣言されていることを確認します。

1. 実際の型名を使用して、デバッガーで変数をキャストではなく`typedef`-定義名。