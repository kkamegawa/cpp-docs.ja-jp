---
title: 独自のヘルパー関数の作成
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
ms.openlocfilehash: 73b4a8180345dd6f7dc26f4243f6e63eda80e4af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293798"
---
# <a name="developing-your-own-helper-function"></a>独自のヘルパー関数の作成

独自のバージョンの DLL またはインポートの名前に基づく特定の処理を実行するルーチンを提供することがあります。 これを行う 2 つの方法がある: に基づいて指定されたコード、コーディング、独自またはだけで説明した通知フックを使用して、指定されたバージョンをフックします。

## <a name="code-your-own"></a>独自のコードします。

これは、機能は、新しいをガイドラインとして指定されたコードを使用することができます基本的にため非常に単純です。 もちろん、呼び出し元の規則に従う必要があり、適切な関数ポインターを返す必要があります、リンカーによって生成されたサンクに返された場合。 1 回、コードにほとんど何でも呼び出しを満たすためか、呼び出しから取得するために実行できます。

## <a name="use-the-start-processing-notification-hook"></a>通知フックの処理開始を使用します。

単に通知 dliStartProcessing で既定のヘルパーと同じ値を受信する通知のユーザーが指定したフック関数への新しいポインターを提供する最も簡単なことが考えられます。 その時点では、フック関数を実質的に新しいヘルパー関数と正常に返された既定のヘルパーには既定のヘルパーのそれ以降のすべての処理をバイパスします。

## <a name="see-also"></a>関連項目

[リンカーによる DLL の遅延読み込み](linker-support-for-delay-loaded-dlls.md)
