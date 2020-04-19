---
title: コネクション ポイント
ms.date: 11/19/2018
f1_keywords:
- IConnectionPoint
helpviewer_keywords:
- IConnectionPoint interface
- connections, connection points
- OLE COM connection points
- MFC COM, connection points
- COM, connection points
- interfaces, IConnectionPoint
- MFC, COM support
- connection points [MFC]
- CCmdTarget class [MFC], and connection points
- sinks, connection points
ms.assetid: bc9fd7c7-8df6-4752-ac8c-0b177442c88d
ms.openlocfilehash: 6f934c4a5a24c5d54805a60e81cb0afdcdc2c14a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153314"
---
# <a name="connection-points"></a>コネクション ポイント

この記事は、(以前は OLE コネクション ポイントと呼ばれます) の接続ポイントを実装する方法を説明します MFC クラスを使用して`CCmdTarget`と`CConnectionPoint`します。

以前は、コンポーネント オブジェクト モデル (COM) に汎用的なメカニズムが定義されている (`IUnknown::QueryInterface`*) を実装し、インターフェイスで機能を公開するオブジェクトを許可します。 ただし、特定のインターフェイスを呼び出すには、機能を公開するオブジェクトを許可されている対応するメカニズムが定義されていません。 COM がオブジェクトにポインターを受信する方法を定義する、(そのオブジェクトのインターフェイスへのポインター) が処理されましたが、発信インターフェイス (ポインターが他のオブジェクトのインターフェイスへのオブジェクトを保持) の明示的なモデルがありませんでした。 COM は、この機能をサポートするモデル、接続のポイントと呼ばれるようになりました。

接続で 2 つの部分: ソースとのインターフェイスを実装するオブジェクトと呼ばれるインターフェイスを呼び出すオブジェクトには、シンクが呼び出されます。 接続ポイントは、ソースによって公開されるインターフェイスです。 接続ポイントを公開するでは、ソースは、シンク自体 (ソース) への接続の確立を許可します。 コネクション ポイント機構 (、`IConnectionPoint`インターフェイス)、ソース オブジェクトに、シンク インターフェイスへのポインターが渡されます。 このポインターは、一連のメンバー関数のシンクの実装にアクセス権を持つソースを提供します。 たとえば、シンクによって実装されるイベントを発生させるには、ソースは、シンクの実装の適切なメソッドを呼び出すことができます。 次の図は、接続を示して説明したポイント。

![接続ポイントを実装](../mfc/media/vc37lh1.gif "接続ポイントの実装") <br/>
コネクション ポイントの実装

MFC 実装では、このモデル、 [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)と[CCmdTarget](../mfc/reference/ccmdtarget-class.md)クラス。 派生したクラス`CConnectionPoint`実装、`IConnectionPoint`インターフェイス、その他のオブジェクトへの接続ポイントを公開するために使用します。 派生したクラス`CCmdTarget`実装、`IConnectionPointContainer`インターフェイスでは、すべてのオブジェクトの使用可能な接続ポイントを列挙または特定の接続ポイントを見つけることができます。

クラスで実装されたコネクション ポイントごとに、接続ポイントを実装する接続の部分を宣言する必要があります。 1 つまたは複数の接続ポイントを実装する場合は、クラスで 1 つの接続マップを宣言することも必要があります。 コネクション マップは、ActiveX コントロールでサポートされる接続ポイントのテーブルです。

次の例では、単純な接続のマップと 1 つの接続ポイントを示します。 最初の例で、接続のマップとポイント;2 番目の例では、マップとポイントを実装します。 なお`CMyClass`必要があります、 `CCmdTarget`-クラスを派生します。 最初の例では、コードが挿入される、クラス宣言の下、**保護**セクション。

[!code-cpp[NVC_MFCConnectionPoints#1](../mfc/codesnippet/cpp/connection-points_1.h)]

**BEGIN_CONNECTION_PART**と**END_CONNECTION_PART**マクロ、埋め込みのクラスを宣言する`XSampleConnPt`(から派生した`CConnectionPoint`)、この特定の接続ポイントを実装します。 オーバーライドする場合`CConnectionPoint`メンバー関数または独自のメンバー関数を追加、これら 2 つのマクロの間、それらを宣言します。 たとえば、`CONNECTION_IID`マクロよりも優先、`CConnectionPoint::GetIID`これら 2 つのマクロの間に配置した場合、メンバー関数。

2 番目の例では、コントロールの実装ファイル (.cpp ファイル) でコードが挿入されます。 このコードの実装接続ポイントを含む接続マップ`SampleConnPt`:

[!code-cpp[NVC_MFCConnectionPoints#2](../mfc/codesnippet/cpp/connection-points_2.cpp)]

1 つ以上の接続ポイントし、追加の挿入があるかどうかは**CONNECTION_PART**マクロの間、 **BEGIN_CONNECTION_MAP**と**END_CONNECTION_MAP**マクロ。

最後への呼び出しを追加`EnableConnections`クラスのコンス トラクター内。 例:

[!code-cpp[NVC_MFCConnectionPoints#3](../mfc/codesnippet/cpp/connection-points_3.cpp)]

このコードが挿入されると、 `CCmdTarget`-派生クラスの接続ポイントを公開する、`ISampleSink`インターフェイス。 次の図は、この例を示します。

![MFC を使用して実装されたコネクション ポイント](../mfc/media/vc37lh2.gif "MFC を使用して実装されたコネクション ポイント") <br/>
MFC で実装されたコネクション ポイント

接続ポイントが「マルチキャスト」をサポートする、通常は、同じインターフェイスに接続する複数のシンクにブロードキャストする機能。 次の例のフラグメントは、マルチキャスト コネクション ポイントで各シンクを反復処理する方法。

[!code-cpp[NVC_MFCConnectionPoints#4](../mfc/codesnippet/cpp/connection-points_4.cpp)]

この例では、接続の現在のセットを取得、`SampleConnPt`接続ポイントへの呼び出しが`CConnectionPoint::GetConnections`します。 接続および呼び出しで反復処理し、`ISampleSink::SinkFunc`アクティブな接続ごとにします。

## <a name="see-also"></a>関連項目

[MFC COM](../mfc/mfc-com.md)
