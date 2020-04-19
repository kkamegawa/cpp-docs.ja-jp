---
title: 式ステートメント
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
ms.openlocfilehash: 2973c3e0a1cd59edfc7ef1e771454b780da23cf9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400605"
---
# <a name="expression-statement"></a>式ステートメント

式ステートメントを使用すると、式が評価されます。 式ステートメントの結果として、制御が移動したり、イテレーションが発生したりすることはありません。

式ステートメントの構文は、次のように、単純です。

## <a name="syntax"></a>構文

```
[expression ] ;
```

## <a name="remarks"></a>Remarks

式ステートメント内の式はすべて評価され、次のステートメントが実行される前にすべての副作用が完了します。 最も一般的に使用される式ステートメントは、代入と関数呼び出しです。  セミコロンだけと呼ばれる空の式ステートメントと見なされます、式は省略可能であるため、 [null](../cpp/null-statement.md)ステートメント。

## <a name="see-also"></a>関連項目

[C++ ステートメントの概要](../cpp/overview-of-cpp-statements.md)