---
title: bss_seg プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
ms.openlocfilehash: a343fb45b4bbe4789f38b7a1102572cf4241ec53
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218551"
---
# <a name="bss_seg-pragma"></a>bss_seg プラグマ

初期化されていない変数がオブジェクト (.obj) ファイルに格納されるセクション (セグメント) を指定します。

## <a name="syntax"></a>構文

> **#pragma bss_seg (** ["*section-name*" [ **,** "*section-class*"]] **)** \
> **#pragma bss_seg (** { **push** | **pop** } [ **,** *identifier* ] [ **,** "*section-name*" [ **,** "*section-class*"]] **)**

### <a name="parameters"></a>パラメーター

**押し付け**\
Optional内部コンパイラスタックにレコードを格納します。 **プッシュ**は*識別子*と*セクション名*を持つことができます。

**ショート**\
Optional内部コンパイラスタックの先頭からレコードを削除します。 **Pop**は*識別子*と*セクション名*を持つことができます。 *識別子*を使用して、 **pop**コマンドを1つだけ使用して複数のレコードをポップできます。 *セクション名*は、pop の後のアクティブな BSS セクション名になります。

*識別子*\
Optional**Push**と共に使用すると、内部コンパイラスタックのレコードに名前が割り当てられます。 **Pop**と共に使用する場合、ディレクティブは、*識別子*が削除されるまで、レコードを内部スタックからポップします。 *識別子*が内部スタックで見つからない場合は、何もポップされません。

*"section-name"* \
Optionalセクションの名前。 **Pop**と共に使用すると、スタックがポップされ、*セクション名*がアクティブな BSS セクション名になります。

*"セクション-クラス"* \
Optionalは無視されますが、バージョン2.0 よりC++前のバージョンの Microsoft との互換性のために含まれています。

## <a name="remarks"></a>Remarks

オブジェクトファイルの*セクション*は、1つの単位としてメモリに読み込まれるデータの名前付きブロックです。 *BSS セクション*は、初期化されていないデータを含むセクションです。 この記事では、*セグメント*と*セクション*は同じ意味を持ちます。

**Bss_seg** pragma ディレクティブは、初期化されていないすべてのデータ項目を、翻訳単位から*セクション名*という名前の bss セクションに配置するようコンパイラに指示します。 場合によっては、 **bss_seg**を使用すると、初期化されていないデータを1つのセクションにグループ化することで読み込み時間を短縮できます。 既定では、オブジェクトファイル内の初期化されていないデータ`.bss`に使用される BSS セクションにはという名前が付けられます。 **Bss_seg**プラグマディレクティブが指定されていない場合は、その後に初期化されてい`.bss`ないデータ項目の bss セクション名をにリセットします。

**Bss_seg**プラグマを使用して割り当てられたデータは、その場所に関する情報を保持しません。

セクションの作成に使用しない名前の一覧については、「 [/SECTION](../build/reference/section-specify-section-attributes.md)」を参照してください。

初期化されたデータ ([data_seg](../preprocessor/data-seg.md))、関数 ([code_seg](../preprocessor/code-seg.md))、および const 変数 ([const_seg](../preprocessor/const-seg.md)) のセクションを指定することもできます。

DUMPBIN を使用でき[ます。](../build/reference/dumpbin-command-line.md)オブジェクトファイルを表示する EXE アプリケーション。 サポートされている各ターゲットアーキテクチャの DUMPBIN のバージョンは、Visual Studio に含まれています。

## <a name="example"></a>例

```cpp
// pragma_directive_bss_seg.cpp
int i;                     // stored in .bss
#pragma bss_seg(".my_data1")
int j;                     // stored in .my_data1

#pragma bss_seg(push, stack1, ".my_data2")
int l;                     // stored in .my_data2

#pragma bss_seg(pop, stack1)   // pop stack1 from stack
int m;                     // stored in .my_data1

int main() {
}
```

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
