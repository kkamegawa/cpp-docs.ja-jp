---
title: カスタム文字列マネージャーの実装 (詳細方法)
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
ms.openlocfilehash: 3854ffe205aa8e6cb9cfb800b9aa1473094fffaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235500"
---
# <a name="implementation-of-a-custom-string-manager-advanced-method"></a>カスタム文字列マネージャーの実装 (詳細方法)

特殊な状況は、メモリの割り当てに使用されるヒープを変更する以上の処理をカスタム文字列マネージャーを実装する可能性があります。 このような状況である必要があります手動で実装する、 [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md)として、カスタム文字列マネージャーのインターフェイス。

これを行うには、最初に理解しておく必要がどのように[CStringT](../atl-mfc-shared/reference/cstringt-class.md)そのインターフェイスを使用して、文字列データを管理します。 すべてのインスタンス`CStringT`へのポインターを持つ、 [CStringData](../atl-mfc-shared/reference/cstringdata-class.md)構造体。 この可変長構造体には、文字列の実際の文字データだけでなく、文字列 (長さ) などの重要な情報が含まれています。 すべてのカスタム文字列マネージャーは、割り当てと解放の要求でこれらの構造体の`CStringT`します。

`CStringData`構造体は、4 つのフィールドを構成します。

- [pStringMgr](../atl-mfc-shared/reference/cstringdata-class.md#pstringmgr)このフィールドを指す、`IAtlStringMgr`インターフェイスがこの文字列のデータを管理するために使用します。 ときに`CStringT`再割り当てまたは割り当てまたは渡す、このインターフェイスの無料のメソッドを呼び出して、文字列バッファーを解放する必要があります、`CStringData`をパラメーターとして構造体。 割り当てるときに、`CStringData`構造文字列マネージャーで、カスタム文字列マネージャー をポイントするには、このフィールドを設定する必要があります。

- [nDataLength](../atl-mfc-shared/reference/cstringdata-class.md#ndatalength)このフィールドには、現在の論理終端の null を除く、バッファーに格納された文字列の長さが含まれています。 `CStringT` 文字列の長さが変更されたときに、このフィールドを更新します。 割り当てるときに、`CStringData`構造体には、文字列の上司する必要がありますこのフィールドを 0 に設定します。 再割り当てするとき、`CStringData`構造、カスタム文字列マネージャーはこのフィールドは変更しないでを残す必要があります。

- [nAllocLength](../atl-mfc-shared/reference/cstringdata-class.md#nalloclength) (終端の null を除く) に再割り当てすることがなく、この文字列バッファーに格納できる文字の最大数がこのフィールドに含まれています。 たびに`CStringT`論理、文字列の長さを拡張する必要がありますまずバッファーに十分な領域があるかどうかを確認するには、このフィールドを確認します。 チェックが失敗した場合、`CStringT`に、カスタム文字列マネージャーの呼び出しは、バッファーの再割り当ています。 割り当てまたは再割り当てするとき、`CStringData`構造体を設定する必要ありますこれで要求された文字数以上にフィールド、*文字数*パラメーターを[IAtlStringMgr::Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#allocate)または[IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate)します。 要求よりも、バッファーにより多くの領域がある場合は、実際の使用可能な領域の量を反映するようにこの値を設定することができます。 これにより、`CStringT`バッファーの再割り当てする文字列のマネージャーにコールバックする前に、文字列全体を拡張する領域を割り当てられています。

- [nRefs](../atl-mfc-shared/reference/cstringdata-class.md#nrefs)このフィールドには、文字列バッファーの現在の参照カウントが含まれています。 値が 1 つは、次の 1 つのインスタンスの場合`CStringT`バッファーを使用しています。 さらにのインスタンスは、読み取りし、バッファーの内容の変更の両方が許可されます。 値が 1 より大きい場合の複数のインスタンス`CStringT`バッファーを使用することができます。 文字バッファーが共有されるため、`CStringT`インスタンスでは、バッファーの内容を読み取ることができますのみです。 内容を変更する`CStringT`最初、バッファーのコピーを作成します。 場合は、値が負、1 つだけ`CStringT`バッファーを使用しています。 この場合、バッファーと見なされますロックされています。 ときに、`CStringT`インスタンスは、バッファーを使用して、ロックの他のインスタンスがない`CStringT`バッファーを共有することがあります。 代わりに、これらのインスタンスは、内容を操作する前に、バッファーのコピーを作成します。 さらに、`CStringT`ロックされているバッファーを使用して、インスタンスは、他のバッファーを共有しようとはしません`CStringT`に割り当てられているインスタンス。 ここで、`CStringT`インスタンスがロックされているバッファーに、その他の文字列をコピーします。

   割り当てるときに、`CStringData`構造、バッファーで許可されている共有の種類を反映するように、このフィールドを設定する必要があります。 ほとんどの実装の場合は、この値を 1 つに設定します。 これにより、通常の書き込み時コピーの共有動作です。 ただし、文字列の上司が文字列バッファーの共有をサポートしていない場合は、このフィールドをロック状態に設定します。 これにより、`CStringT`のみのインスタンスにこのバッファーを使用する`CStringT`割り当てることです。

## <a name="see-also"></a>関連項目

[CStringT によるメモリ管理](../atl-mfc-shared/memory-management-with-cstringt.md)
