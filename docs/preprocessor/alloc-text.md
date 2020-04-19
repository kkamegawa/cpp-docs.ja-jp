---
title: alloc_text プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
ms.openlocfilehash: 7ddb12b39e068dea42f7a47f7fd937424be43725
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216343"
---
# <a name="alloc_text-pragma"></a>alloc_text プラグマ

指定した関数定義が存在するコード セクションに名前を付けます。 このプラグマは、名前付き関数の関数宣言子と関数定義との間で指定する必要があります。

## <a name="syntax"></a>構文

> **#pragma alloc_text (** "*textsection*" **,** *function1* [ **,** *function2* ...] **)**

## <a name="remarks"></a>Remarks

**Alloc_text**プラグマは、メンバー C++関数またはオーバーロードされた関数を処理しません。 これは、C リンケージ (つまり、 **extern "C"** リンケージ仕様で宣言された関数) で宣言された関数にのみ適用できます。 C++ リンケージを持つ関数でこのプラグマを使用しようとすると、コンパイラ エラーが生成されます。

を使用`__based`した関数のアドレス指定はサポートされていないため、セクションの場所を指定するには、 **alloc_text**プラグマを使用する必要があります。 *Textsection*によって指定された名前は、二重引用符で囲む必要があります。

**Alloc_text**プラグマは、指定された関数の宣言の後、およびこれらの関数の定義の前に記述する必要があります。

**Alloc_text**プラグマで参照される関数は、プラグマと同じモジュールで定義する必要があります。 それ以外の場合、定義されていない関数が後で別のテキストセクションにコンパイルされると、エラーがキャッチされるか、またはキャッチされない可能性があります。 プログラムは正常に動作しますが、関数は目的のセクションでは割り当てられません。

**Alloc_text**に関するその他の制限は次のとおりです。

- 関数内では使用できません。

- 関数が宣言された後で、関数が定義される前に使用する必要があります。

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
