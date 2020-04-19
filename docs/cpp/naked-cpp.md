---
title: naked (C++)
ms.date: 11/04/2016
f1_keywords:
- naked_cpp
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
ms.openlocfilehash: 951760d7f9566c084bbe3d5a574d006020576c61
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345005"
---
# <a name="naked-c"></a>naked (C++)

**Microsoft 固有の仕様**

宣言されている関数、 **naked**属性に、コンパイラは、プロローグおよびエピローグ コードなしのコードを生成します。 この機能を使用して、プロローグとエピローグのコード シーケンスをインライン アセンブラー コードで独自に記述できます。 naked 関数は、仮想デバイス ドライバーの記述用に特に便利です。  なお、 **naked**属性は x86 と ARM でのみ有効ですし、x64 では使用できません。

## <a name="syntax"></a>構文

```
__declspec(naked) declarator
```

## <a name="remarks"></a>Remarks

**Naked**属性は関数の定義に関連するのみであり、型修飾子ではない、naked 関数は、拡張属性構文を使用する必要があります、 [_ _declspec](../cpp/declspec.md)キーワード。

関数も付いて場合でも、コンパイラが、naked 属性でマークされた関数のインライン関数を生成することはできません、 [_ _forceinline](inline-functions-cpp.md)キーワード。

場合、コンパイラがエラーを発行、 **naked**属性メンバーではないメソッドの定義以外のすべてに適用されます。

## <a name="examples"></a>使用例

このコードで関数を定義する、 **naked**属性。

```
__declspec( naked ) int func( formal_parameters ) {}
```

または、次のようにします。

```
#define Naked __declspec( naked )
Naked int func( formal_parameters ) {}
```

**Naked**属性が、関数のプロローグとエピローグ シーケンスのコンパイラのコード生成の性質のみに影響します。 このような関数を呼び出すために生成されるコードには影響を与えません。 つまり、 **naked**属性は、関数の型の一部と見なされますしないと、関数ポインターを持つことはできません、 **naked**属性。 さらに、 **naked**属性は、データの定義に適用できません。 たとえば、次のサンプル コードはエラーになります。

```
__declspec( naked ) int i;
// Error--naked attribute not permitted on data declarations.
```

**Naked**属性は、関数の定義のみに関連し、関数のプロトタイプでは指定できません。 たとえば、次の宣言はコンパイラ エラーになります。

```
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__declspec](../cpp/declspec.md)<br/>
[キーワード](../cpp/keywords-cpp.md)<br/>
[naked 関数呼び出し](../cpp/naked-function-calls.md)