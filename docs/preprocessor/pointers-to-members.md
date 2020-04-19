---
title: pointers_to_members プラグマ
ms.date: 08/29/2019
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
ms.openlocfilehash: 6058e3e4855eb745a01410e31eb9f454ef131ab1
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821409"
---
# <a name="pointers_to_members-pragma"></a>pointers_to_members プラグマ

**C++のみ**

クラスメンバーへのポインターを、関連付けられているクラス定義の前に宣言できるかどうかを指定します。 ポインターのサイズ、およびポインターを解釈するために必要なコードを制御するために使用されます。

## <a name="syntax"></a>構文

> **#pragma pointers_to_members (** *ポインター宣言*[ **、** *最も一般的な表現*])

## <a name="remarks"></a>Remarks

[/Vmb または/vmg](../build/reference/vmb-vmg-representation-method.md)コンパイラオプションや[継承キーワード](../cpp/inheritance-keywords.md)を使用する代わりに、ソースファイルに**pointers_to_members**プラグマを配置できます。

*ポインター宣言*引数は、関連付けられている関数定義の前または後に、メンバーへのポインターを宣言したかどうかを指定します。 *ポインター宣言*引数は、次の2つの記号のいずれかになります。

| 引数 | コメント |
|--------------|--------------|
| **full_generality** | 安全な、場合によっては最適でないコードです。 メンバーへのポインターが、関連付けられているクラス定義の前に宣言されている場合は、 **full_generality**を使用します。 この引数は、*最も汎用表現*の引数で指定されたポインター表現を常に使用します。 これは /vmg と同じです。 |
| **best_case** | メンバーへのすべてのポインターに対し、最適な表現を使用した安全で最適なコードを生成します。 クラスのメンバーへのポインターを宣言する前に、クラスを定義する必要があります。 既定値は**best_case**です。 |

*最も一般的*な引数は、変換単位のクラスのメンバーへのポインターを参照するためにコンパイラが安全に使用できる最小のポインター表現を指定します。 引数には、次のいずれかの値を指定できます。

| 引数 | コメント |
|--------------|--------------|
| **single_inheritance** | 最も一般的な表現は、単一継承、メンバー関数へのポインターです。 メンバーへのポインターが宣言されているクラス定義の継承モデルが多重継承モデルまたは仮想モデルの場合、エラーが発生します。 |
| **multiple_inheritance** | 最も一般的な表現は、多重継承、メンバー関数へのポインターです。 メンバーへのポインターが宣言されているクラス定義の継承モデルが仮想モデルの場合、エラーが発生します。 |
| **virtual_inheritance** | 最も一般的な表現は、仮想継承、メンバー関数へのポインターです。 エラーが発生することはありません。 `#pragma pointers_to_members(full_generality)` を使用する場合、 **virtual_inheritance**は既定の引数です。 |

> [!CAUTION]
> **Pointers_to_members**プラグマは、`#include` ディレクティブの後にのみ、影響を与えるソースコードファイル内に配置することをお勧めします。 これにより、プラグマが他のファイルに影響を与えるリスクが軽減され、同じ変数、関数、またはクラス名に対して複数の定義が誤って指定されます。

## <a name="example"></a>使用例

```cpp
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

**特定C++の終了**

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __pragma キーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
