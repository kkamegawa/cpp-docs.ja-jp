---
title: scanf での文字幅指定
ms.date: 10/22/2019
api_location:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- scanf
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
ms.openlocfilehash: 54331f4150c50b084b59ac51b3f34ffe15c5b1c8
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811122"
---
# <a name="scanf-width-specification"></a>scanf での文字幅指定

この情報は、`scanf_s` など、安全なバージョンを含む `scanf` 関数ファミリの書式指定文字列の解釈に適用されます。 これらの関数は通常、入力ストリームが一連のトークンに分割されていることを前提とします。 トークンは、空白 (スペース、タブ、または改行) で区切られます。数値型の場合は、数値テキストに変換できない最初の文字によって示される数値データ型の自然な終端によって区切られます。 ただし、幅指定を使用すると、トークンの自然な終了の前に入力の解析が停止することがあります。

*width* 指定は、`%` と型フィールド指定子 (*width* フィールドと呼ばれる正の整数を含む) との間の文字、およびフィールドのサイズを示す 1 つ以上の文字で構成されます。後者は、整数型が **short** または **long** のどちらであるかを示すなどの、フィールドの型の修飾子ともみなされます。 このような文字はサイズのプレフィックスと呼ばれます。

## <a name="the-width-field"></a>[幅] フィールド

*Width*フィールドは、そのフィールドに対して読み取る最大文字数を制御する正の10進整数です。 対応する `argument`には、*全角*文字以下が変換されて格納されます。 指定された書式に従って変換できない空白文字または文字が、*幅*に達する前に出現する場合は、*幅*がより小さい文字が読み取られます。

幅の指定は、これらの関数のセキュリティで保護されたバージョン (たとえば、`scanf_s`、`wscanf_s`など) に必要なバッファーサイズ引数とは別のものです。 次の例では、幅指定は 20 であり、入力ストリームから 20 文字までが読み取られることを示してます。 バッファー長は 21 であり、入力可能な 20 文字の空きと、null 終端文字が含まれています。

```C
char str[21];
scanf_s("%20s", str, 21);
```

*Width*フィールドが使用されていない場合、`scanf_s` は、トークン全体の文字列への読み取りを試行します。 指定されたサイズがトークン全体を保持するのに十分な大きさではない場合、対象の文字列には何も書き込まれません。 *Width*フィールドが指定されている場合、トークン内の最初の*幅*の文字が、null ターミネータと共にコピー先の文字列に書き込まれます。

## <a name="the-size-prefix"></a>サイズプレフィックス

省略可能なプレフィックス**h**、 **hh**、 **l**、 **ll**、 **I64**、 **l**は、`argument` (変更する型文字に応じて、long または short、1バイト文字またはワイド文字) のサイズを示します。 これらの書式指定文字列は、`scanf` または `wscanf` 関数で使用され、次の表に示す引数の解釈を指定します。 型プレフィックス**I64**は Microsoft 拡張機能であり、標準 C と互換性がありません。型文字とその意味については、scanf 関数の[型フィールド文字](../c-runtime-library/scanf-type-field-characters.md)の「scanf 関数の型文字」の表を参照してください。

> [!NOTE]
> **H**、 **l**、および**l**プレフィックスは、 **char**型のデータと共に使用する場合の Microsoft 拡張機能です。

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Scanf と wscanf の書式指定子のサイズプレフィックス

|指定する型|プリフィックス|型指定子|
|----------------|----------------|-------------------------|
|**double**|**l**|**e**、**E**、**f**、**g**、または **G**|
|**long double** (double と同じ)|**L**|**e**、**E**、**f**、**g**、または **G**|
|**long int**|**l**|**d**、**i**、**o**、**x**、または **X**|
|**long unsigned int**|**l**|**u**|
|**long long**|**ll**|**d**、**i**、**o**、**x**、または **X**|
|**short int**|**h**|**d**、**i**、**o**、**x**、または **X**|
|**short unsigned int**|**h**|**u**|
|**char**|**hh**|**d**、**i**、**o**、**x**、または **X**|
|**unsigned char**|**hh**|**u**|
|**int64**|**I64**|**d**、**i**、**o**、**u**、**x**、または **X**|
|1 バイト文字と `scanf`|**h**|**c** または **C**|
|1 バイト文字と `wscanf`|**h**|**c** または **C**|
|ワイド文字と `scanf`|**l**|**c** または **C**|
|ワイド文字と `wscanf`|**l**|**c** または **C**|
|1バイト文字の文字列と `scanf`|**h**|**s** または **S**|
|1バイト文字の文字列と `wscanf`|**h**|**s** または **S**|
|`scanf` を含むワイド文字列|**l**|**s** または **S**|
|`wscanf` を含むワイド文字列|**l**|**s** または **S**|

次の例では、**h** と **l** を `scanf_s` 関数と `wscanf_s` 関数で使用します:

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

`scanf` ファミリの安全でない関数を使用する場合は、前の引数のバッファー長を示すサイズ パラメーターを省略します。

## <a name="reading-undelimited-strings"></a>区切られていない文字列の読み取り

空白で区切られていない文字列を読み取るには、角かっこ内の文字セット ( **[ ]** ) を **s** (文字列) 型の文字に代用できます。 角かっこ内の文字のセットは、*制御文字列*と呼ばれます。 対応する入力フィールドは、コントロール文字列に表示されない最初の文字まで読み取られます。 セット内の最初の文字がカレット ( **^** ) の場合、効果は逆になり、入力フィールドは文字セットの残りの部分に表示される最初の文字までが読み取られます。

% [A-z **]** と **% [z-a]** は、どちらも **% [abcde...z...z]** 。 これは一般的な `scanf` 関数の拡張機能ですが、標準 C では必須ではありません。

## <a name="reading-unterminated-strings"></a>未終了の文字列の読み取り

終端の null 文字 (' \ 0 ') を格納せずに文字列を格納するには、指定 `%Nc`を使用します。ここで、 *N*は10進整数です。 この場合、**c** の型文字は引数が文字配列へのポインターであることを示します。 次の*N*文字が入力ストリームから指定された場所に読み取られ、null 文字 (' \ 0 ') は追加されません。 *N*が指定されていない場合の既定値は1です。

## <a name="when-scanf-stops-reading-a-field"></a>scanf がフィールドの読み取りを停止するタイミング

`scanf`関数は文字単位で入力フィールドをスキャンします。 次のいずれかの理由により、空白文字に到達する前に特定の入力フィールドの読み取りを停止する場合があります。

- 指定した幅に到達しました。

- 次の文字は、指定されたとおりに変換できません。

- 次の文字が、一致すると考えられる制御文字列内の文字と競合しています。

- 次の文字が特定の文字セットに表示されません。

理由に関係なく、`scanf` 関数が入力フィールドの読み取りを停止すると、次の入力フィールドは、最初の未読文字から始まるとみなされます。 競合する文字 (存在する場合) は、未読と見なされます。 これは、次の入力フィールドの最初の文字、または入力ストリームに対する後続の読み取り操作の最初の文字です。

## <a name="see-also"></a>関連項目

[scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[書式指定フィールド: scanf 関数と wscanf 関数](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[scanf 関数の型フィールド文字](../c-runtime-library/scanf-type-field-characters.md)<br/>
