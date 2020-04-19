---
title: C ビット フィールド
ms.date: 11/04/2016
helpviewer_keywords:
- bitfields
- bit fields
ms.assetid: 9faf74c4-7fd5-4b44-ad18-04485193d06e
ms.openlocfilehash: 62c982fa078182cb1902b6770f0a3713ca4ff7a8
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150234"
---
# <a name="c-bit-fields"></a>C ビット フィールド

構造体または共用体のメンバーの宣言子に加えて、構造体の宣言子も "ビット フィールド" と呼ばれる指定のビット数になります。 その長さは、フィールド名の宣言子からコロンによって区切られます。 ビット フィールドは整数型として解釈されます。

## <a name="syntax"></a>構文

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declarator*<sub>opt</sub> **:** *constant-expression*

*constant-expression* は、フィールドの幅 (ビット単位) を指定します。 `declarator` の *type-specifier* は、`unsigned int`、**signed int**、または `int` である必要があります。*constant-expression* は負ではない整数値である必要があります。 値がゼロの場合、宣言には `declarator` がありません。 ビット フィールド、ビット フィールドへのポインター、およびビット フィールドを返す関数の配列は使用できません。 省略可能な `declarator` はビット フィールドの名前を指定します。 ビット フィールドは構造体の一部としてしか宣言できません。 アドレス演算子 (**&**) は、ビット フィールド コンポーネントに適用できません。

名前のないビット フィールドは参照できません。実行時の内容は予測できません。 これらはアラインメントのために "ダミー" フィールドとして使用できます。 幅が 0 として指定された、名前のないビット フィールドは、*struct-declaration-list* 内でそれに続くメンバーのストレージが、`int` 境界で開始されることを保証します。

ビット フィールドは、ビット パターンを含めるための十分な長さを持つ必要があります。 たとえば、次の 2 つのステートメントは正しくありません。

```
short a:17;        /* Illegal! */
int long y:33;     /* Illegal! */
```

次の例では、`screen` という名前の構造体の 2 次元配列を定義します。

```
struct
{
    unsigned short icon : 8;
    unsigned short color : 4;
    unsigned short underline : 1;
    unsigned short blink : 1;
} screen[25][80];
```

配列には 2,000 の要素が含まれます。 各要素は、`icon`、`color`、`underline`、および `blink` の 4 つのビット フィールド メンバーを含む個別の構造体です。 各構造体のサイズは 2 バイトです。

ビット フィールドには、整数型と同じセマンティクスがあります。 これは、ビット フィールドにあるビット数にかかわらず、同じ基本型の変数が使用される場合とまったく同じように、式でビット フィールドが使用されることを意味します。

**Microsoft 固有の仕様**

`int` として定義されたビット フィールドは、符号付きとして扱われます。 ANSI C 規格への Microsoft 拡張機能を使用すると、ビット フィールドに対して `char` および **long** 型 (**Signed** と `unsigned` の両方) が許されます。 **long**、**short**、または `char` (**Signed** または `unsigned`) 基本型の名前のないビット フィールドは、基本型に適した境界に強制的にアラインメントされます。

ビット フィールドは、整数内で最下位ビットから最上位ビットへと割り当てられます。 次のコードでは、

```
struct mybitfields
{
    unsigned short a : 4;
    unsigned short b : 5;
    unsigned short c : 7;
} test;

int main( void );
{
    test.a = 2;
    test.b = 31;
    test.c = 0;
}
```

ビットは次のように配置されます。

```
00000001 11110010
cccccccb bbbbaaaa
```

8086 ファミリのプロセッサは整数値の下位バイトを上位バイトの前に格納するため、上記の整数 `0x01F2` は、後に `0xF2` が続く `0x01` として物理メモリに格納されます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[構造体宣言](../c-language/structure-declarations.md)
