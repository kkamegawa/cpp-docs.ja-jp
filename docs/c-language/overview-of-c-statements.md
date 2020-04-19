---
title: C ステートメントの概要
ms.date: 11/04/2016
helpviewer_keywords:
- semicolon, in C statements
- statements, C
- semicolon
- statements, about statements
- Visual C, statements
ms.assetid: 0d49837a-5399-4881-b60c-af5f4e9720de
ms.openlocfilehash: bfa6840553055202f26f55e1dc5971bfd047b2de
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857074"
---
# <a name="overview-of-c-statements"></a>C ステートメントの概要

C ステートメントは、トークン、式、および他のステートメントで構成されます。 別のステートメントの構成要素となるステートメントは、外側のステートメントの "本体" と呼ばれます。 このセクションでは、次の構文で示されたステートメントの種類それぞれについて説明します。

## <a name="syntax"></a>構文

*statement*: [labeled-statement](../c-language/goto-and-labeled-statements-c.md)

[compound-statement](../c-language/compound-statement-c.md)

[expression-statement](../c-language/expression-statement-c.md)

[selection-statement](../c-language/if-statement-c.md)

[iteration-statement](../c-language/do-while-statement-c.md)

[jump-statement](../c-language/break-statement-c.md)

[try-except-statement](../c-language/try-except-statement-c.md) /* Microsoft 固有の \*/

[try-finally ステートメント](../c-language/try-finally-statement-c.md) /\* Microsoft 固有の \*/

ステートメント本体が "複合ステートメント" であることはよくあります。 複合ステートメントは、キーワードも含めて、他のステートメントで構成されます。 複合ステートメントは、中かっこ ( **{ }** ) で区切られます。 他の C ステートメントはすべてセミコロン ( **;** ) で終了します。 セミコロンはステートメントの終端記号です。

式ステートメントは、「[式と代入](../c-language/expressions-and-assignments.md)」で説明されている算術演算子または論理演算子を含むことができる C 式を含みます。 null ステートメントは空のステートメントです。

どの C ステートメントも、名前とコロンで構成される識別ラベルを先頭に置くことができます。 ステートメント ラベルを認識するのは `goto` ステートメントだけであるため、ステートメント ラベルについては `goto` と一緒に説明しています。 詳細については、「[goto ステートメントとラベル付きステートメント](../c-language/goto-and-labeled-statements-c.md)」を参照してください。

## <a name="see-also"></a>参照

[ステートメント](../c-language/statements-c.md)
