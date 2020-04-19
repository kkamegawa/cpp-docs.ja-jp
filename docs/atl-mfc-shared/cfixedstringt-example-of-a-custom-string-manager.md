---
title: CFixedStringT:カスタム文字列マネージャーの使用例
ms.date: 11/04/2016
helpviewer_keywords:
- CFixedStringT class, using a custom string manager
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
ms.openlocfilehash: 2b6da5d4166b220ef63500d0154ab32dc72b40f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209878"
---
# <a name="cfixedstringt-example-of-a-custom-string-manager"></a>CFixedStringT:カスタム文字列マネージャーの使用例

ATL ライブラリ クラスで使用されるカスタム文字列マネージャーの 1 つの例の実装[CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md)という**CFixedStringMgr**します。 `CFixedStringT` 派生[CStringT](../atl-mfc-shared/reference/cstringt-class.md)実装の一部としてその文字データによって割り当てられる文字列と、`CFixedStringT`オブジェクト自体が、文字列で指定された長さよりも小さい場合に限り、 `t_nChars` のテンプレートパラメーター`CFixedStringT`. この方法で、文字列必要はありません、ヒープ、文字列の長さが固定バッファーのサイズを超えない場合を除き。 `CFixedStringT`ヒープの文字列データの割り当てを常にではありませんを使用しないは使用できません`CAtlStringMgr`その文字列のマネージャーとして。 カスタム文字列マネージャーを使用する (`CFixedStringMgr`)、実装、 [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md)インターフェイス。 このインターフェイスは、後ほど[、カスタム文字列マネージャーの実装 (メソッドの高度な)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)します。

コンス トラクター`CFixedStringMgr`は 3 つのパラメーターを受け取ります。

- *pData:* 固定へのポインター`CStringData`構造体を使用します。

- *文字数:* 最大文字数、`CStringData`構造を保持できます。

- *pMgr:* ポインター、 `IAtlStringMgr` "バックアップ文字列 manager"のインターフェイス

コンス トラクターの値を格納する*pData*と*pMgr*内の各メンバー変数 (`m_pData`と`m_pMgr`)。 ゼロに固定のバッファーと-1 に参照カウントの最大サイズと同じ長さの使用可能なバッファーの長さを設定します。 参照カウントの値は、バッファーがロックされていることを示しますのこのインスタンスを使用して`CFixedStringMgr`文字列マネージャーとして。

その他のロックされているバッファーのマークを付けるように`CStringT`からバッファーへの共有の参照を保持しているインスタンス。 他の`CStringT`インスタンスで許可されていることが可能に含まれているバッファーのバッファーを共有`CFixedStringT`中に、その他の文字列バッファーを使用していて削除します。

`CFixedStringMgr` 完全な実装には、`IAtlStringMgr`インターフェイス。 各メソッドの実装は個別に説明します。

## <a name="implementation-of-cfixedstringmgrallocate"></a>CFixedStringMgr::Allocate の実装

実装`CFixedStringMgr::Allocate`文字列の要求されたサイズが固定バッファーのサイズ以下かどうかを最初に確認 (に格納されている、`m_pData`メンバー)。 固定バッファーが十分に大きい場合`CFixedStringMgr`長さ 0 の固定バッファーをロックします。 文字列の長さが固定のバッファーのサイズまで拡張されない限り、`CStringT`バッファーの再割り当てする必要はありません。

文字列の要求されたサイズが固定バッファーより大きいかどうか`CFixedStringMgr`文字列バックアップ マネージャーに要求を転送します。 バックアップの文字列のマネージャーは、ヒープからバッファーを割り当てることと見なされます。 このバッファーを返す前に、ただし、 `CFixedStringMgr` 、バッファーをロックし、バッファーの文字列マネージャーのポインターへのポインターに置き換え、`CFixedStringMgr`オブジェクト。 これにより、再割り当てまたはでバッファーを解放しようとする`CStringT`が呼び出せる`CFixedStringMgr`します。

## <a name="implementation-of-cfixedstringmgrreallocate"></a>CFixedStringMgr::ReAllocate の実装

実装`CFixedStringMgr::ReAllocate`の実装によく似ています`Allocate`します。

再割り当てされるバッファーは固定バッファー、要求されたバッファー サイズが固定バッファーより小さい場合は、割り当ては行われません。 ただし、再割り当てされるバッファーが固定バッファーでない場合、バックアップ マネージャーに割り当てられたバッファーをある必要があります。 ここでバックアップ マネージャーは、バッファーの再割り当てに使用されます。

再割り当てされるバッファーは固定バッファーと、新しいバッファーのサイズが大きすぎて、固定バッファー内に収まる場合`CFixedStringMgr`バックアップ マネージャーを使用して新しいバッファーを割り当てます。 固定バッファーの内容は新しいバッファーにコピーされます。

## <a name="implementation-of-cfixedstringmgrfree"></a>CFixedStringMgr::Free の実装

実装`CFixedStringMgr::Free`と同じパターンに従います`Allocate`と`ReAllocate`します。 固定バッファーが解放されるバッファーには、メソッドにより、長さ 0 のロックされているバッファーを設定します。 バックアップ マネージャーで割り当てられたバッファーが解放される場合`CFixedStringMgr`バックアップ マネージャーを使用して、それを解放します。

## <a name="implementation-of-cfixedstringmgrclone"></a>CFixedStringMgr::Clone の実装

実装`CFixedStringMgr::Clone`バックアップ マネージャーへのポインターを返します常にではなく`CFixedStringMgr`自体。 これはすべてのインスタンスの`CFixedStringMgr`の 1 つのインスタンスに関連付けることができますのみ`CStringT`します。 その他のインスタンスの`CStringT`マネージャーの複製を行おうとする必要がありますバックアップ マネージャーの代わりに表示します。 これは、共有されているバックアップ マネージャーがサポートしているためにです。

## <a name="implementation-of-cfixedstringmgrgetnilstring"></a>CFixedStringMgr::GetNilString の実装

実装`CFixedStringMgr::GetNilString`固定バッファーを返します。 1 対 1 の対応付けのため`CFixedStringMgr`と`CStringT`、特定のインスタンスの`CStringT`一度に 1 つ以上のバッファーを使用することはありません。 そのため、nil の文字列と実際の文字列バッファーは同じ時に必要なことはありません。

固定バッファーが、使用されていないときに`CFixedStringMgr`により、長さが 0 で初期化します。 これにより、nil の文字列として使用することができます。 おまけとして、`nAllocLength`固定バッファーのメンバーは常に完全な固定バッファーのサイズに設定します。 つまり、`CStringT`呼び出さずに文字列を拡張できる[IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate)nil 文字列場合でも、します。

## <a name="requirements"></a>必要条件

**ヘッダー:** cstringt.h

## <a name="see-also"></a>関連項目

[CStringT によるメモリ管理](../atl-mfc-shared/memory-management-with-cstringt.md)
