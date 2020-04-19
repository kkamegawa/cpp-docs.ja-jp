---
title: CComBSTR を使用したプログラミング (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
ms.openlocfilehash: 806d23730a0657fc1e0c154e20dc9abd62f7e8af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261814"
---
# <a name="programming-with-ccombstr-atl"></a>CComBSTR を使用したプログラミング (ATL)

ATL クラス[CComBSTR](../atl/reference/ccombstr-class.md) BSTR データ型ラッパーを提供します。 中に`CComBSTR`便利なツールは、注意を必要とするいくつかの状況があります。

- [変換の問題](#programmingwithccombstr_conversionissues)

- [範囲の問題](#programmingwithccombstr_scopeissues)

- [CComBSTR オブジェクトを明示的に解放します。](#programmingwithccombstr_explicitlyfreeing)

- [ループで CComBSTR オブジェクトを使用](#programmingwithccombstr_usingloops)

- [メモリ リークの問題](#programmingwithccombstr_memoryleaks)

##  <a name="programmingwithccombstr_conversionissues"></a> 変換の問題

いくつか`CComBSTR`メソッドが Unicode に ANSI 文字列引数を自動的に変換されます、メソッドは常に Unicode 形式の文字列を返します。 出力文字列を ANSI に変換する、するには、ATL 変換クラスを使用します。 ATL 変換クラスの詳細については、次を参照してください。 [ATL と MFC 文字列変換マクロ](reference/string-conversion-macros.md)します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]

変更する、文字列リテラルを使用している場合、`CComBSTR`オブジェクト、ワイド文字の文字列を使用します。 これにより、不要な変換が減少します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]

##  <a name="programmingwithccombstr_scopeissues"></a> 範囲の問題

任意のクラスを適切に動作と同様`CComBSTR`スコープ外になったときにそのリソースが解放されます。 関数へのポインターを返す場合、`CComBSTR`文字列では、この問題が発生、ポインターは、既に解放されたメモリを参照するためです。 このような場合、`Copy`メソッドは、次のようです。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]

##  <a name="programmingwithccombstr_explicitlyfreeing"></a> CComBSTR オブジェクトを明示的に解放します。

含まれる文字列を明示的に解放することができます、`CComBSTR`オブジェクトのオブジェクトがスコープ外に出る前にします。 文字列が解放される場合、`CComBSTR`オブジェクトが無効です。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]

##  <a name="programmingwithccombstr_usingloops"></a> ループで CComBSTR オブジェクトを使用

として、`CComBSTR`クラスは、特定の操作を実行します。 バッファーを割り当て、`+=`演算子または`Append`メソッドには使用しないで、緊密なループ内で文字列の操作を実行することです。 このような場合は、`CStringT`パフォーマンスが優れています。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]

##  <a name="programmingwithccombstr_memoryleaks"></a> メモリ リークの問題

初期化のアドレスを渡す`CComBSTR`として機能する、 **[out]** メモリ リークを発生させます。

文字列を保持するために次の例で、文字列が割り当てられている`"Initialized"`リークした場合に、関数`MyGoodFunction`は、文字列を置換します。

[!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]

メモリ リークを避けるためには、呼び出し、`Empty`メソッドを既存の`CComBSTR`オブジェクトとしてアドレスを渡す前に、 **[out]** パラメーター。

エントリの場合は、関数のパラメーターが、同じコードは、リークが発生しませんに注意してください。 **[で, out]** します。

## <a name="see-also"></a>関連項目

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[CStringT クラス](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[wstring](../standard-library/basic-string-class.md)<br/>
[文字列変換に関するマクロ](../atl/reference/string-conversion-macros.md)
