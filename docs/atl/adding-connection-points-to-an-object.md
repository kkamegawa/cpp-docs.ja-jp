---
title: オブジェクトへの接続ポイントの追加
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], adding to ATL objects
- Implement Connection Point ATL wizard
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
ms.openlocfilehash: 7341e69852ed804122e0196b51d305f5af0c35b9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223520"
---
# <a name="adding-connection-points-to-an-object"></a>オブジェクトへの接続ポイントの追加

[ATL チュートリアル](../atl/active-template-library-atl-tutorial.md)コネクション ポイントのサポートでコントロールを作成する方法、イベントを追加する方法、および接続ポイントを実装する方法を示します。 ATL 接続ポイントでは、 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)クラス。

接続ポイントを実装するには、2 つの選択肢があります。

- コントロールまたはオブジェクトに接続ポイントを追加することで、独自の送信のイベント ソースを実装します。

- 別のタイプ ライブラリで定義されている接続ポイントのインターフェイスを再利用します。

いずれの場合も、接続ポイントの実装ウィザードはタイプ ライブラリを使用して、その作業を行います。

### <a name="to-add-a-connection-point-to-a-control-or-object"></a>コントロールまたはオブジェクトへの接続ポイントを追加するには

1. .Idl ファイルのライブラリ ブロックにディスパッチ インターフェイスを定義します。 コネクション ポイントのサポートを有効にした場合、ATL コントロール ウィザードを使用して、コントロールを作成したときに、ディスパッチ インターフェイス既にに作成します。 コントロールの作成時に接続ポイントのサポートを有効にしなかった、.idl ファイルにディスパッチ インターフェイスを手動で追加する必要があります。 次は、ディスパッチ インターフェイスの例です。 発信インターフェイスがディスパッチ インターフェイスである必要はありませんが、VBScript や JScript などの多くのスクリプト言語ではこれが要求されるため、この例は、2 つのディスパッチ インターフェイスを使用しています。

   [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/cpp/adding-connection-points-to-an-object_1.idl)]

   Uuidgen.exe または guidgen.exe ユーティリティを使用すると、GUID を生成します。

2. ディスパッチ インターフェイスとしての追加、`[default,source]`プロジェクトの .idl ファイル内のオブジェクトのコクラスのインターフェイス。 ここでも、コントロールを作成するときに、コネクション ポイントのサポートが有効にした場合、ATL コントロール ウィザードが作成、 `[default,source`] エントリ。 このエントリを手動で追加するには、太字で、行を追加します。

   [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/cpp/adding-connection-points-to-an-object_2.idl)]

   .Idl ファイルを参照して、[円](../overview/visual-cpp-samples.md)例については、ATL のサンプルです。

3. クラス ビューを使用して、イベント インターフェイスにメソッドとプロパティを追加します。 クラス ビュー内のクラスを右クリックし、**追加**をクリックし、ショートカット メニュー**接続ポイントの追加**します。

4. **ソース インターフェイス**の実装接続ポイントのウィザード、[選択] リスト ボックス**インターフェイス**します。 キーを押して、コントロールのインターフェイスを選択するかどうかは**OK**は。

   - イベントの呼び出しを送信すると、コードを実装するイベントのプロキシ クラスをヘッダー ファイルを生成します。

   - 接続ポイントのマップ エントリを追加します。

   タイプ ライブラリのすべての一覧は、コンピューターにも表示されます。 これら他のタイプ ライブラリの 1 つは、別のタイプ ライブラリで検出された正確な同じ送信インターフェイスを実装する場合、接続ポイントを定義にのみ使用する必要があります。

### <a name="to-reuse-a-connection-point-interface-defined-in-another-type-library"></a>別のタイプ ライブラリで定義されている接続ポイントのインターフェイスを再利用するには

1. クラス ビューでは、実装するクラスを右クリックし、 **BEGIN_COM_MAP**マクロ、 をポイント**追加**をクリックし、ショートカット メニュー**接続ポイントの追加**します。

2. 接続ポイントの実装ウィザードでタイプ ライブラリのタイプ ライブラリとインターフェイスを選択し、をクリックして**追加**します。

3. .Idl ファイルを編集します。

   - ディスパッチ インターフェイスは、イベント ソースが使用されているオブジェクトの .idl ファイルからコピーします。

   - 使用して、 **importlib**そのタイプ ライブラリに命令します。

## <a name="see-also"></a>関連項目

[接続ポイント](../atl/atl-connection-points.md)
