---
title: 推論規則
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: 0c1db9150c3b2c36c35e6802bfcd639af45bdc82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291276"
---
# <a name="inference-rules"></a>推論規則

推論規則は、コマンド ターゲットを更新およびターゲットの依存関係を推論するを指定します。 推論規則の拡張機能が 1 つのターゲットと一致し、同じ基本名がある依存します。 推論規則には、ユーザー定義または定義済みです。定義済みの規則を再定義することができます。

コマンド、古いの依存関係がない場合、[します。サフィックス](dot-directives.md)依存ファイルの拡張子と一致するターゲットと、既存のルールが現在または指定したディレクトリにファイル (nmake の) 使用されます。 1 つ以上のルールが、既存のファイルと一致する場合、**します。サフィックス**リストを使用して、決定; 一覧の優先順位は左から右にします。 依存ファイルが存在しないが別の記述ブロックのターゲットとして表示されない場合は、推論規則から作成できます不足している依存する別のファイルと同じベース名に置き換えます。 記述ブロックのターゲットには、依存ファイルやコマンドがなければ、推論規則は、ターゲットを更新できます。 推論規則は、記述ブロックが存在しない場合でも、コマンド ライン ターゲットをビルドできます。 (Nmake の) は、明示的な依存ファイルが指定した場合でも、推論による依存ファイルのルールを呼び出すことができます。

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

[ルールを定義します。](defining-a-rule.md)

[バッチモード規則](batch-mode-rules.md)

[定義済みの規則](predefined-rules.md)

[推論による依存ファイルと規則](inferred-dependents-and-rules.md)

[推論規則の優先順位](precedence-in-inference-rules.md)

## <a name="see-also"></a>関連項目

[NMAKE リファレンス](nmake-reference.md)