---
title: IDispEventImpl のサポート
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
ms.openlocfilehash: 3652aae2a6c84833ed32e52599d3834d6e66a5ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274288"
---
# <a name="supporting-idispeventimpl"></a>IDispEventImpl のサポート

テンプレート クラスは、 [IDispEventImpl](../atl/reference/idispeventimpl-class.md) ATL クラスでのコネクション ポイントのシンクのサポートを提供するために使用できます。 コネクション ポイントのシンクには、外部の COM オブジェクトから発生したイベントを処理するために、クラスができます。 これらの接続ポイント シンクは、クラスによって提供される、イベント シンク マップにマップされます。

クラスのコネクション ポイントのシンクを正しく実装するには、次の手順を実行する必要があります。

- 各外部オブジェクトのタイプ ライブラリをインポートします。

- 宣言、`IDispEventImpl`インターフェイス

- イベント シンク マップを宣言します。

- 通知の接続ポイントをアドバイズと

コネクション ポイントのシンクを実装するための手順はすべて、のみのヘッダー ファイル (.h) クラスを変更することで実現します。

## <a name="importing-the-type-libraries"></a>タイプ ライブラリをインポートします。

各外部のオブジェクトを処理するイベントのタイプ ライブラリをインポートする必要があります。 この手順では、処理できるイベントを定義し、イベント シンク マップを宣言するときに使用される情報を提供します。 [#Import](../preprocessor/hash-import-directive-cpp.md)ディレクティブは、これを実現するために使用できます。 追加するために必要な`#import`ディレクティブの行をクラスのヘッダー ファイル (.h) をサポートする各ディスパッチ インターフェイス。

次の例は、外部の COM サーバーのタイプ ライブラリをインポート (`MSCAL.Calendar.7`)。

[!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]

> [!NOTE]
>  個別の必要`#import`ステートメントをサポートする各外部タイプ ライブラリ。

## <a name="declaring-the-idispeventimpl-interfaces"></a>IDispEventImpl インターフェイスの宣言

ディスパッチ インターフェイスごとのタイプ ライブラリをインポートしたら、これで個別に宣言する必要があります。`IDispEventImpl`各外部ディスパッチ インターフェイスのインターフェイス。 追加することで、クラスの宣言を変更、`IDispEventImpl`インターフェイス外部オブジェクトごとに宣言します。 パラメーターの詳細については、次を参照してください。 [IDispEventImpl](../atl/reference/idispeventimpl-class.md)します。

次のコードの 2 つのコネクション ポイント シンクを宣言する、`DCalendarEvents`クラスによって実装される COM オブジェクトのインターフェイス、 `CMyCompositCtrl2`:

[!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]

## <a name="declaring-an-event-sink-map"></a>イベント シンク マップを宣言します。

イベント通知は、適切な関数で処理するためには、クラスは、適切なハンドラーを各イベントをルーティングする必要があります。 これは、イベント シンク マップを宣言することによって実現されます。

ATL には、いくつかのマクロ[BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map)、 [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map)、および[SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex)、このマッピングを容易にします。 標準の形式は次のとおりです。

```cpp
BEGIN_SINK_MAP(comClass)
  SINK_ENTRY_EX(id, iid, dispid, func)
  . . . //additional external event entries
END_SINK_MAP()
```

次の例では、2 つのイベント ハンドラーでイベント シンク マップで宣言します。

[!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]

実装はほぼ完了です。 最後の手順では、通知と外部インターフェイスのアドバイズを中止を扱います。

## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>IDispEventImpl のインターフェイスをアドバイズと

最後の手順では、適切なタイミングでは (アドバイズするか、) すべてのコネクション ポイント メソッドを実装します。 外部のクライアントと、オブジェクト間の通信を行う前に、このアドバイスを実行する必要があります。 オブジェクトが表示される前に、オブジェクトでサポートされている外部のディスパッチ インターフェイスは各発信インターフェイスが照会されます。 接続が確立されているし、アウトゴーイング インターフェイスへの参照がオブジェクトからのイベントを処理するために使用します。 この手順は「通知」と呼ばれます

外部インターフェイスを持つオブジェクトが完了したら、発信インターフェイスはクラスでは使用されなく通知する必要があります。 このプロセスは「アドバイズ」と呼ばれます

COM オブジェクトの一意な性質では、この手順は異なりますの詳細と実装間での実行。 これらの詳細は、このトピックの範囲を超えています、対応していません。

## <a name="see-also"></a>関連項目

[ATL COM オブジェクトの基礎](../atl/fundamentals-of-atl-com-objects.md)
