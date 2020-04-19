---
title: C ストレージ クラス
ms.date: 08/31/2018
helpviewer_keywords:
- static variables, lifetime
- storage classes
- lifetime, variables
- specifiers, storage class
- storage class specifiers, C storage classes
- storage duration
ms.assetid: 893fb929-f7a9-43dc-a0b3-29cb1ef845c1
ms.openlocfilehash: 77aefe41fecf003218343710ef090eebf99446a8
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857113"
---
# <a name="c-storage-classes"></a>C ストレージ クラス

変数の "ストレージ クラス" は、項目が "グローバルな" 有効期間を持つか、"ローカルな" 有効期間を持つかを決定します。 C では、これら 2 つの有効期間を "static" および "automatic" と呼びます。 グローバル有効期間を持つ項目は、プログラムの実行全体に値があります。 すべての関数にはグローバル有効期間があります。

ローカル有効期間を持つ自動変数、または変数は、自分が定義されているブロックに実行制御が渡されるたびに新しいストレージが割り当てられます。 実行から返るとき、変数には有効な値が含まれていません。

C には、次のストレージ クラス指定子が用意されています。

## <a name="syntax"></a>構文

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**auto**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**register**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**static**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**typedef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *拡張宣言-seq* **)**  /\* Microsoft 固有の \*/

`__declspec` を除いて、宣言の *declaration-specifier* では 1 個の *storage-class-specifier* のみ使用できます。 ストレージ クラスの指定が行われない場合、ブロック内の宣言により自動オブジェクトが作成されます。

**auto** または **register** 指定子で宣言された項目にはローカルの有効期間があります。 **static** または `extern` 指定子で宣言された項目にはグローバルの有効期間があります。

`typedef` および `__declspec` は他の 4 つの *storage-class-specifier* 終端要素とは意味が異なるため、個別に説明しています。 `typedef` の具体的な情報については、「[Typedef Declarations (Typedef の宣言)](../c-language/typedef-declarations.md)」をご覧ください。 `__declspec` の具体的な情報については、[拡張ストレージ クラス属性](../c-language/c-extended-storage-class-attributes.md)に関するページをご覧ください。

ソース ファイル内の変数と関数宣言の配置は、ストレージ クラスと可視性にも影響します。 すべての関数定義の外部にある宣言は、"外部レベル" での記述と呼ばれます。 関数定義内での宣言は、"内部レベル" で記述されます。

各ストレージ クラス指定子の厳密な意味は 2 つの要因に左右されます。

- 宣言が現れるのが、外部レベルか内部レベルか

- 宣言された項目が、変数または関数であるかどうか

「[Storage-Class Specifiers for External-Level Declarations (外部レベル宣言のストレージ クラス指定子)](../c-language/storage-class-specifiers-for-external-level-declarations.md)」および「[Storage-Class Specifiers for Internal-Level Declarations (内部レベル宣言のストレージ クラス指定子)](../c-language/storage-class-specifiers-for-internal-level-declarations.md)」では、各種宣言の *storage-class-specifier* 終端要素について記載し、変数から *storage-class-specifier* が省略されている場合の既定の動作について説明しています。 「[Storage-Class Specifiers with Function Declarations (関数宣言を伴うストレージ クラス指定子)](../c-language/storage-class-specifiers-with-function-declarations.md)」では、関数と共に使用されるストレージ クラス指定子について説明します。

## <a name="see-also"></a>参照

[宣言と型](../c-language/declarations-and-types.md)
