---
title: 条件式演算子
ms.date: 11/04/2016
helpviewer_keywords:
- conditional operators
- operators [C++], conditional
- expressions [C++], conditional
ms.assetid: c4f1a5ca-0844-44a7-a384-eca584d4e3dd
ms.openlocfilehash: 9dc93a47d36af92fe370e3f56f504682d49bd1dd
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150624"
---
# <a name="conditional-expression-operator"></a>条件式演算子

C 言語では、三項演算子として条件式演算子 (**? :**) を使用します。

## <a name="syntax"></a>構文

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR expression*  **?**  *expression*  **:**  *conditional-expression*

*logical-OR-expression* には、整数型、浮動小数点型、またはポインター型を指定する必要があります。 この式は、0 に等しいかどうかが評価されます。 シーケンス ポイントは *logical-OR-expression* に従います。 オペランドは次のように評価されます。

- *logical-OR-expression* が 0 でない場合、*expression* が評価されます。 この式の評価結果は、非終端の *expression* として与えられます  (つまり、*logical-OR-expression* が true の場合のみ *expression* が評価されます)。

- *logical-OR-expression* が 0 の場合、*conditional-expression* が評価されます。 この式の結果は *conditional-expression* の値です  (つまり、*logical-OR-expression* が false の場合のみ *conditional-expression* が評価されます)。

*expression* または *conditional-expression* のいずれかが評価されます。両方は評価されません。

条件演算の結果の型は、次のように、*expression* または *conditional-expression* オペランドの型に依存します。

- *expression* または *conditional-expression* が整数型または浮動小数点型の場合 (それぞれ型が異なる可能性があります)、この演算子は通常の算術変換を実行します。 結果の型は、変換後のオペランドの型です。

- *expression* と *conditional-expression* が両方とも同じ構造体型、共用体型、またはポインター型の場合、演算結果はそれと同じ構造体型、共用体型、またはポインター型になります。

- 両方のオペランドが `void` 型の場合、結果は `void` 型になります。

- 一方のオペランドが任意の型のオブジェクトへのポインターであり、もう一方のオペランドが `void` へのポインターである場合、そのオブジェクトへのポインターが `void` へのポインターに変換され、結果は `void` へのポインターになります。

- *expression* または *conditional-expression* のいずれかがポインターであり、もう一方のオペランドが値 0 の定数式である場合、結果はポインター型になります。

ポインターの型を比較する際、ポインターが指している型の型修飾子 (**const** または `volatile`) は重要ではありません。ただし、結果の型は、条件式を構成する両方の要素の型修飾子を継承します。

## <a name="examples"></a>使用例

次に、条件演算子の使用例を示します。

```
j = ( i < 0 ) ? ( -i ) : ( i );
```

この例では、`i` の絶対値を `j` に代入します。 `i` が 0 未満の場合、`-i` が `j` に代入されます。 `i` が 0 以上の場合、`i` が `j` に代入されます。

```
void f1( void );
void f2( void );
int x;
int y;
    .
    .
    .
( x == y ) ? ( f1() ) : ( f2() );
```

この例では、2 つの関数 `f1` と `f2`、および 2 つの変数 `x` と `y` を宣言しています。 プログラムの後半では、これら 2 つの変数が同じ値の場合に `f1` 関数を呼び出します。 それ以外の場合は `f2` を呼び出します。

## <a name="see-also"></a>関連項目

[条件演算子: ? :](../cpp/conditional-operator-q.md)
