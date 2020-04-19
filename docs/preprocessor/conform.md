---
title: conform プラグマ
ms.date: 08/29/2019
f1_keywords:
- conform_CPP
- vc-pragma.conform
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
ms.openlocfilehash: 816ff85bb19f549c6ea072073bd89fcd503545f2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220501"
---
# <a name="conform-pragma"></a>conform プラグマ

**C++のみ**

[/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)コンパイラオプションの実行時の動作を指定します。

## <a name="syntax"></a>構文

> **#pragma 準拠**している (*名前* **[, show]** [ **,** { **on** | **off** }] [[ **,** { **push** | **pop** }] [ **,** *identifier* [ **,** { **on** **オフ}** ]  | ] ] **)**

### <a name="parameters"></a>パラメーター

*指定*\
変更されるコンパイラ オプションの名前を指定します。 有効な*名前*は`forScope`だけです。

**示**\
Optional*名前*の現在の設定 (true または false) を、コンパイル中に警告メッセージで表示します。 たとえば、`#pragma conform(forScope, show)` のようにします。

**on**、 **off**\
Optional*名前*を**on**に設定すると、 [/zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)コンパイラオプションが有効になります。 既定値は**off**です。

**押し付け**\
Optional*名前*の現在の値を内部コンパイラスタックにプッシュします。 *識別子*を指定すると、スタックにプッシュされる*名前*の**on**または**off**の値を指定できます。 たとえば、`#pragma conform(forScope, push, myname, on)` のようにします。

**ショート**\
Optional*Name*の値を内部コンパイラスタックの一番上の値に設定し、スタックをポップします。 識別子を**pop**と共に指定すると、*識別子*を持つレコードが見つかるまでスタックがポップされます。これもポップされます。スタック上の次のレコードの [*名前*] の現在の値が、[*名前*] の新しい値になります。 スタック上のレコードに含まれていない*識別子*を使用して**pop**を指定すると、 **pop**は無視されます。

*識別子*\
Optional**プッシュ**または**pop**コマンドに含めることができます。 *識別子*を使用する場合は、 **on**または**off**指定子も使用できます。

## <a name="example"></a>例

```cpp
// pragma_directive_conform.cpp
// compile with: /W1
// C4811 expected
#pragma conform(forScope, show)
#pragma conform(forScope, push, x, on)
#pragma conform(forScope, push, x1, off)
#pragma conform(forScope, push, x2, off)
#pragma conform(forScope, push, x3, off)
#pragma conform(forScope, show)
#pragma conform(forScope, pop, x1)
#pragma conform(forScope, show)

int main() {}
```

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
