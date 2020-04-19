---
title: ATL ウィンドウの特徴
ms.date: 11/04/2016
helpviewer_keywords:
- window traits
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
ms.openlocfilehash: 29549e54051405fc3dd4d5d7ae70a382ad7a62ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196184"
---
# <a name="understanding-window-traits"></a>ウィンドウの特徴を理解します。

ウィンドウの特性クラスは、ATL ウィンドウ オブジェクトを作成するために使用するスタイルを標準化するための単純なメソッドを提供します。 ウィンドウの特徴は、テンプレート パラメーターとして受け入れられます[CWindowImpl](../atl/reference/cwindowimpl-class.md)と既定のクラス レベルでのウィンドウ スタイルを指定するための手段として他の ATL ウィンドウ クラス。

ウィンドウのインスタンスの作成者がへの呼び出しで明示的にスタイルを指定しない場合[作成](../atl/reference/cwindowimpl-class.md#create)、特性クラスを使用して、適切なスタイルを使用して、ウィンドウが作成されます。 でも、特定のスタイルに設定されているウィンドウ クラスのすべてのインスタンスの他のスタイルを許容しつつ、インスタンスごとの単位で設定を確保できます。

## <a name="atl-window-traits-templates"></a>ATL ウィンドウの特徴のテンプレート

ATL には、テンプレート パラメーターを使用して、コンパイル時に既定のスタイルを設定するための 2 つのウィンドウの特徴テンプレートが用意されています。

|クラス|説明|
|-----------|-----------------|
|[CWinTraits](../atl/reference/cwintraits-class.md)|既定の呼び出しでその他のスタイルが指定されていない場合にのみ使用されるウィンドウのスタイルを指定する場合に、このテンプレートを使用して`Create`します。 コンパイル時にスタイルの設定より優先の実行時に提供するスタイル。|
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|ウィンドウ クラスの常に設定する必要があるスタイルを指定する場合に、このクラスを使用します。 実行時に提供されているスタイルは、ビットごとの OR 演算子を使用して、コンパイル時に設定するスタイルを使用して結合されます。|

ATL には、多数の定義済みの特殊化のこれらのテンプレートだけでなく、`CWinTraits`ウィンドウ スタイルの組み合わせを一般的に使用されるテンプレート。 参照してください、 [CWinTraits](../atl/reference/cwintraits-class.md)完全な詳細についてはドキュメントを参照します。

## <a name="custom-window-traits"></a>カスタムのウィンドウの特徴

可能性は低い状況では ATL で提供されているテンプレートの 1 つは特化は不十分なため、独自の特性クラスを作成する必要があるだけ 2 つの静的関数を実装するクラスを作成する必要があります:`GetWndStyle`と`GetWndStyleEx`:

[!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]

これらの各関数に渡されるスタイル値を使用して、新しいスタイルの値を生成する実行時。 静的関数に渡されるスタイル値がスタイルの引数として渡されたものする場合は、ウィンドウの特性クラスは、ATL ウィンドウ クラスのテンプレート引数として使用されている、[作成](../atl/reference/cwindowimpl-class.md#create)です。

## <a name="see-also"></a>関連項目

[ウィンドウ クラス](../atl/atl-window-classes.md)
