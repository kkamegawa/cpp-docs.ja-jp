---
title: data_seg プラグマ
ms.date: 08/29/2019
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
ms.openlocfilehash: f67a9f39695adf5067c61288cf09ea7eb481c7dd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220379"
---
# <a name="data_seg-pragma"></a>data_seg プラグマ

初期化された変数がオブジェクト (.obj) ファイルに格納されるデータセクション (セグメント) を指定します。

## <a name="syntax"></a>構文

> **#pragma data_seg (** ["*section-name*" [ **,** "*section-class*"]] **)** \
> **#pragma data_seg (** { **push** | **pop** } [ **,** *identifier* ] [ **,** "*section-name*" [ **,** "*section-class*"]] **)**

### <a name="parameters"></a>パラメーター

**押し付け**\
Optional内部コンパイラスタックにレコードを格納します。 **プッシュ**は*識別子*と*セクション名*を持つことができます。

**ショート**\
Optional内部コンパイラスタックの先頭からレコードを削除します。 **Pop**は*識別子*と*セクション名*を持つことができます。 *識別子*を使用して、 **pop**コマンドを1つだけ使用して複数のレコードをポップできます。 *セクション名*は、pop の後のアクティブなデータセクション名になります。

*識別子*\
Optional**Push**と共に使用すると、内部コンパイラスタックのレコードに名前が割り当てられます。 **Pop**と共に使用すると、*識別子*が削除されるまでレコードを内部スタックからポップします。 *識別子*が内部スタックで見つからない場合は、何もポップされません。

*識別子*を使用すると、複数のレコードを1つの**pop**コマンドでポップできます。

*"section-name"* \
Optionalセクションの名前。 **Pop**と共に使用すると、スタックがポップされ、*セクション名*がアクティブなデータセクション名になります。

*"セクション-クラス"* \
Optionalは無視されますが、バージョン2.0 よりC++前のバージョンの Microsoft との互換性のために含まれています。

## <a name="remarks"></a>Remarks

オブジェクトファイルの*セクション*は、1つの単位としてメモリに読み込まれるデータの名前付きブロックです。 *データセクション*は、初期化されたデータを含むセクションです。 この記事では、*セグメント*と*セクション*は同じ意味を持ちます。

初期化された変数の .obj ファイルの既定の`.data`セクションはです。 初期化されていない変数はゼロに初期化され、 `.bss`に格納されます。

**Data_seg** pragma ディレクティブは、すべての初期化されたデータ項目を、翻訳単位から*セクション名*という名前のデータセクションに配置するようコンパイラに指示します。 既定では、オブジェクトファイル内の初期化されたデータに使用`.data`される data セクションにはという名前が付けられます。 初期化されていない変数は0に初期化されると見なさ`.bss`れ、に格納されます。 **Data_seg**プラグマディレクティブが指定されていない場合は、その後に初期化されるデータ項目`.data`のデータセクション名をにリセットします。

**Data_seg**を使用して割り当てられたデータは、その場所に関する情報を保持しません。

セクションの作成に使用しない名前の一覧については、「 [/SECTION](../build/reference/section-specify-section-attributes.md)」を参照してください。

Const 変数のセクション ([const_seg](../preprocessor/const-seg.md))、初期化されていないデータ ([bss_seg](../preprocessor/bss-seg.md))、および関数 ([code_seg](../preprocessor/code-seg.md)) を指定することもできます。

DUMPBIN を使用でき[ます。](../build/reference/dumpbin-command-line.md)オブジェクトファイルを表示する EXE アプリケーション。 サポートされている各ターゲットアーキテクチャの DUMPBIN のバージョンは、Visual Studio に含まれています。

## <a name="example"></a>例

```cpp
// pragma_directive_data_seg.cpp
int h = 1;                     // stored in .data
int i = 0;                     // stored in .bss
#pragma data_seg(".my_data1")
int j = 1;                     // stored in .my_data1

#pragma data_seg(push, stack1, ".my_data2")
int l = 2;                     // stored in .my_data2

#pragma data_seg(pop, stack1)   // pop stack1 off the stack
int m = 3;                     // stored in .my_data1

int main() {
}
```

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
