---
title: 推論による依存ファイルと推論規則
ms.date: 11/04/2016
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
ms.openlocfilehash: b9c3055db0cc173999e1737986166eb334dcf96c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269909"
---
# <a name="inferred-dependents-and-rules"></a>推論による依存ファイルと推論規則

NMAKE では、該当する推論規則が存在する場合のターゲットの推論による依存ファイルを想定しています。 場合、ルールが適用されます。

- *toext*ターゲットの拡張子に一致します。

- *fromext*一致のターゲットの基本名とを持つファイルの拡張子が現在または指定したディレクトリに存在します。

- *fromext*に[します。サフィックス](dot-directives.md); の他の*fromext*照合ルールではより高度な**します。サフィックス**優先順位。

- 高度な明示的な依存ファイルを持たない**します。サフィックス**優先順位。

推論による依存ファイルには、予期しない副作用が生じる可能性があります。 ターゲットの説明のブロックにコマンドが含まれている場合 (nmake の) は、ルールで、コマンドではなく、これらのコマンドを実行します。

## <a name="see-also"></a>関連項目

[推論規則](inference-rules.md)
