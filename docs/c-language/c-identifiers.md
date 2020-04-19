---
title: C 識別子
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, C
- naming identifiers
- identifiers
- symbols, C identifiers
- identifiers, case sensitivity
- symbols, case sensitivity
ms.assetid: d02edbbc-85a0-4118-997b-84ee6b972eb6
ms.openlocfilehash: 1f3abf304e6fda52e2571d0bccb8d4db5a414dfe
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152587"
---
# <a name="c-identifiers"></a>C 識別子

"識別子" または "シンボル" は、プログラム内の変数、型、関数、およびラベルに対して指定する名前です。 識別子名は、どのキーワードともスペル (大文字小文字の区別を含む) が異なっている必要があります。 キーワード (C または Microsoft) は識別子として使用できません。これらは特別な用途のために予約されています。 識別子を作成するには、変数、型、または関数を定義する際に指定します。 この例では、`result` は整数変数の識別子で、`main` と `printf` は関数の識別子名です。

```
#include <stdio.h>

int main()
{
    int result;

    if ( result != 0 )
        printf_s( "Bad file handle\n" );
}
```

識別子を宣言した後、それ以降のプログラム ステートメントでその識別子を使用して、関連する値を参照できます。

`goto` ステートメントでは、ステートメント ラベルと呼ばれる特殊な識別子を使用できます  (宣言は「[型の宣言](../c-language/declarations-and-types.md)」で説明し、ステートメント ラベルは [goto ステートメントとラベル付きステートメント](../c-language/goto-and-labeled-statements-c.md) に関するページで説明します)。

## <a name="syntax"></a>構文

*identifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *digit*

*nondigit*: 次のいずれか<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**_ a b c d e f g h i j k l mn o p q r s t u v w x y z**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F G H I J K L MN O P Q R S T U V W X Y Z**

*digit*: 次のいずれか<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

識別子名の先頭文字は `nondigit` (つまり、英字の大文字か小文字、またはアンダースコア文字) にする必要があります。 ANSI の規定により、外部識別子の名前では 6 個の有意文字、内部 (関数内) 識別子の名前では 31 個の有意文字を使用できます。 外部識別子 (グローバル スコープで宣言されるか、`extern` ストレージ クラスで宣言された識別子) は、リンカーなど他のソフトウェアで処理する必要があるため、追加の名前付け規約の影響を受ける場合があります。

**Microsoft 固有の仕様**

ANSI では、外部識別子の名前は 6 文字、内部 (関数内部) 識別子の名前は 31 文字と規定されていますが、Microsoft C コンパイラでは、内部または外部の識別子名で 247 文字を使用できます。 ANSI 互換に関して問題がない場合は、/H (外部名の長さを制限する) オプションを使用して、この既定値を大きい数値または小さい数値に変更できます。

**Microsoft 固有の仕様はここまで**

C コンパイラでは、大文字と子文字は別の文字と見なされます。 このように "大文字と小文字が区別" されるので、同じスペルであっても大文字と小文字を変えることで、異なる識別子を作成できます。 たとえば、次の識別子はそれぞれ一意です。

```
add
ADD
Add
aDD
```

**Microsoft 固有の仕様**

識別子に対して、2 個のアンダースコアまたは大文字に続くアンダースコアで始まる名前を選択しないでください。 ANSI C 規格では、これらの文字の組み合わせで始まる識別子名はコンパイラ用に予約されています。 ファイル レベルのスコープを持つ識別子には、先頭の 2 文字にアンダースコアと小文字を使用する名前を付けることもできません。 これらの文字で始まる識別子名も予約されています。 規則では、Microsoft は、マクロ名を開始するには 1 つのアンダースコアおよび大文字を使用し、Microsoft 仕様のキーワード名には二重アンダースコアを使用します。 名前の競合を回避するには、1 つまたは 2 つのアンダースコアで始まらない識別子名、またはアンダースコアで始まり大文字が続く名前を常に選択します。

**Microsoft 固有の仕様はここまで**

次は、ANSI または Microsoft の命名制限に準拠する有効な識別子の例です。

```
j
count
temp1
top_of_page
skip12
LastNum
```

**Microsoft 固有の仕様**

ソース ファイルの識別子では既定で大文字と小文字が区別されますが、オブジェクト ファイルのシンボルでは区別されません。 Microsoft C は大文字と小文字を区別してコンパイル単位内の ID を処理します。

Microsoft リンカーでは大文字と小文字が区別されます。 ケースに従って、すべての識別子を一貫して指定する必要があります。

"ソース文字セット" は、ソース ファイルに表示できる有効な文字のセットです。 Microsoft C では、ソース セットは標準 ASCII 文字セットです。 ソース文字セットおよび実行文字セットには、エスケープ シーケンスとして使用される ASCII 文字が含まれます。 実行文字セットについては、[文字定数](../c-language/c-character-constants.md)に関するページをご覧ください。

**Microsoft 固有の仕様はここまで**

識別子には "スコープ" と "リンケージ" があります。スコープはプログラムが認識される範囲です。リンケージは、別のスコープ内の同じ名前が同じ識別子を参照するかどうかを決定します。 これらのトピックについては、「[有効期間、スコープ、可視性、およびリンケージ](../c-language/lifetime-scope-visibility-and-linkage.md)」で説明します。

## <a name="see-also"></a>関連項目

[C の要素](../c-language/elements-of-c.md)
