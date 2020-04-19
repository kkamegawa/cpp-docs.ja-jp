---
title: インターネット上の ActiveX コントロール
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX controls [MFC], creating
- ActiveX controls [MFC], Internet
- downloading data with ActiveX controls
- OLE controls [MFC], upgrading to ActiveX
- Internet applications [MFC], ActiveX controls
- networks [MFC], downloading with ActiveX controls
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
ms.openlocfilehash: d268da8bef4facfb9259e6ce43648c8713464ec9
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448192"
---
# <a name="activex-controls-on-the-internet"></a>インターネット上の ActiveX コントロール

ActiveX コントロールは、更新されたバージョンの OLE コントロールの仕様です。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

コントロールは、さまざまなインターネット上の COM 対応の Web ブラウザーなど、別のコンテナーで使用できるプログラミング可能なソフトウェア コンポーネントを開発するための基本的なアーキテクチャです。 ActiveX コントロールことができます、インターネット コントロールし、アクティブなドキュメントにその機能を追加したり Web ページの一部にします。 Web ページ上のコントロールは、スクリプトを使用して相互に通信できます。

ActiveX コントロールは、インターネットに限定されません。 コントロールがそのコンテナーに必要なインターフェイスをサポートしていれば、任意のコンテナーで ActiveX コントロールを使用こともできます。

**ActiveX コントロールなど、いくつかの利点があります。**

- インターフェイスは、以前の OLE コントロールよりも少ない必要です。

- ウィンドウなしで使用可能と常にで実行中です。

**ActiveX コントロールをするためには、コントロールが必要です。**

- サポート、`IUnknown`インターフェイス。

- COM オブジェクトであります。

- エクスポート**DLLRegisterServer**と**DLLUnRegisterServer**します。

- 機能の必要に応じて追加のインターフェイスをサポートします。

## <a name="making-your-existing-controls-internet-friendly"></a>既存のコントロールをインターネット対応にします。

インターネット環境で適切に動作するコントロールをデザインすると、相対的に低い伝送速度のインターネット上の考慮事項が必要です。 既存のコントロールを使用することができます。ただし、コードのサイズを小さくし、コントロール プロパティを非同期的にダウンロードを実行する手順があります。

コントロールのパフォーマンスを向上させるのには、次のヒントを参考に、効率性に関する考慮事項を実行します。

- この記事で説明する手法を実装[ActiveX コントロール。最適化](../mfc/mfc-activex-controls-optimization.md)します。

- コントロールがインスタンス化する方法を検討してください。

- 非同期です。その他のプログラムを保持しません。

- 小さなブロック内のデータをダウンロードします。

   ビットマップ、ビデオ データなどの大きなストリームをダウンロードするときに、コンテナーとの連携で非同期的にコントロールのデータにアクセスします。 データも取得する他のコントロールと協調して、増分または連続的な方法でデータを取得します。 コードは、非同期的にもダウンロードできます。

- コードとプロパティをバック グラウンドでダウンロードできます。

- ユーザー インターフェイスになるできる限り迅速にアクティブです。

- 検討してください (ビットマップ画像やビデオ データ) などのプロパティと大規模なデータの両方が Blob 永続的なデータの格納方法。

   大きなビットマップなど、AVI ファイルの永続的なデータの量が大幅にコントロールでは、ダウンロードの方法に注意が必要です。 ドキュメントまたはページはできるだけ早く表示になるし、コントロールがバック グラウンドでデータを取得中に、ページと対話するユーザーを許可します。

- コードのサイズを保持し、実行時間を短くするために、効率的なルーチンを記述します。

   永続的なデータは、わずか数バイトで、小規模のボタンとラベル コントロールは、ブラウザー内で、作業とインターネット環境で使用するために適しています。

- コンテナーに進行状況の通知を検討してください。

   など、ユーザーは、ページとの対話を開始できると、ダウンロードが完了すると、非同期のダウンロードの進行中のコンテナーに通知します。 コンテナーを表示できます進行状況 (% 完了) とユーザー。

- クライアント コンピューターのコントロールを登録する方法を検討してください。

## <a name="creating-a-new-activex-control"></a>新しい ActiveX コントロールを作成します。

アプリケーション ウィザードを使用して、新しいコントロールを作成するときに非同期モニカーとその他の最適化を有効にすることもできます。 コントロールのプロパティを非同期的にダウンロードするサポートを追加するには、次の手順を実行します。

#### <a name="to-create-your-project-using-the-mfc-activex-control-wizard"></a>MFC ActiveX コントロール ウィザードを使用してプロジェクトを作成するには

1. クリックして**新規**上、**ファイル**メニュー。

1. 選択**MFC ActiveX コントロール ウィザード**Visual Studio からC++プロジェクトし、プロジェクトの名前します。

1. **コントロール設定**] ページで、[**プロパティを非同期的に読み込みます**します。 このオプションを選択する準備完了状態プロパティおよび状態変更イベントを設定します。

   など、その他の最適化を選択することもできます。**ウィンドウなしのアクティベーション**、に記載されている[ActiveX コントロール。最適化](../mfc/mfc-activex-controls-optimization.md)します。

1. 選択**完了**プロジェクトを作成します。

#### <a name="to-create-a-class-derived-from-cdatapathproperty"></a>CDataPathProperty から派生したクラスを作成するには

1. 派生したクラスを作成する`CDataPathProperty`します。

1. 各コントロールのヘッダー ファイルを含むソース ファイルでは、その前に、このクラスのヘッダー ファイルを追加します。

1. このクラスでオーバーライド`OnDataAvailable`します。 この関数は、データが表示されるたびに呼び出されます。 データが使用可能になるとは、任意の方法、たとえば段階的にレンダリングして処理できます。

   次に示すコードでは、段階的にデータを表示するための編集コントロールでの単純な例を示します。 フラグの使用に注意してください**BSCF_FIRSTDATANOTIFICATION**エディット コントロールをオフにします。

   [!code-cpp[NVC_MFCActiveXControl#1](../mfc/codesnippet/cpp/activex-controls-on-the-internet_1.cpp)]

   AFXCMN を含める必要があることに注意してください。使用する H、`CListCtrl`クラス。

1. コントロールの全体的な状態が変化 (たとえば、読み込みに初期化されたまたはユーザーから対話型)、呼び出し`COleControl::InternalSetReadyState`します。 コードを追加するには、コントロールに 1 つのデータ パスのプロパティがある場合は、**知らせる**ダウンロードが完了したコンテナーに通知します。 例:

   [!code-cpp[NVC_MFCActiveXControl#2](../mfc/codesnippet/cpp/activex-controls-on-the-internet_2.cpp)]

1. `OnProgress` をオーバーライドします。 `OnProgress`最大範囲を示す数値が渡される、および現在のダウンロードが完了するまでどの番号が表示されました。 これらの番号を使用すると、ユーザーに達成率などの状態を表示します。

次の手順では、した派生クラスを使用するコントロールにプロパティを追加します。

#### <a name="to-add-a-property"></a>プロパティを追加するには

1. **クラス ビュー**ライブラリ ノードの下にインターフェイスを右クリックし、選択、**追加**、し**プロパティの追加**します。 これは、開始、**プロパティの追加ウィザード**します。

1. **プロパティの追加ウィザード**を選択、**の設定/取得方法**ラジオ ボタン、型、**プロパティ名**EditControlText、として選択BSTRなど、**プロパティ型**します。

1. **[完了]** をクリックします。

1. メンバー変数を宣言、 `CDataPathProperty`-ActiveX コントロール クラスにクラスを派生します。

   [!code-cpp[NVC_MFCActiveXControl#3](../mfc/codesnippet/cpp/activex-controls-on-the-internet_3.h)]

1. 
  `Get/Set` メソッドを実装します。 `Get`文字列を返します。 `Set`、プロパティと呼び出しを読み込む`SetModifiedFlag`します。

   [!code-cpp[NVC_MFCActiveXControl#4](../mfc/codesnippet/cpp/activex-controls-on-the-internet_4.cpp)]

1. [DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange)、次の行を追加します。

   [!code-cpp[NVC_MFCActiveXControl#5](../mfc/codesnippet/cpp/activex-controls-on-the-internet_5.cpp)]

1. オーバーライド[ResetData](../mfc/reference/cdatapathproperty-class.md#resetdata)この行を追加してコントロールをリセットするプロパティに通知します。

   [!code-cpp[NVC_MFCActiveXControl#6](../mfc/codesnippet/cpp/activex-controls-on-the-internet_6.cpp)]

## <a name="deciding-whether-to-derive-from-cdatapathproperty-or-ccacheddatapathproperty"></a>CDataPathProperty またはプロパティから派生するかどうかを決定します。

前の例は、コントロールのプロパティから派生する手順を説明します。`CDataPathProperty`します。 これは、頻繁に変更されると、すべてのデータが、現在の値のみを保持する必要のない、リアルタイムのデータをダウンロードしている場合に、適切な選択です。 例は、株価表示器コントロールです。

派生することもできます。`CCachedDataPathProperty`します。 この場合は、ダウンロードされたデータは、メモリ ファイルにキャッシュされます。 これは、ダウンロードしたすべてのデータを保持する必要がある場合の適切な選択肢 — たとえば、段階的にビットマップをレンダリングするコントロール。 この場合は、クラスには、データを含むメンバー変数があります。

`CMemFile m_Cache;`

このメモリ マップト ファイルを使用する ActiveX コントロール クラスで`OnDraw`データを表示します。 ActiveX コントロールで`CCachedDataPathProperty`-派生クラスでメンバー関数をオーバーライド`OnDataAvailable`し、基本クラスの実装を呼び出した後、コントロールを無効にします。

[!code-cpp[NVC_MFCActiveXControl#7](../mfc/codesnippet/cpp/activex-controls-on-the-internet_7.cpp)]

## <a name="downloading-data-asynchronously-using-activex-controls"></a>非同期的に ActiveX コントロールを使用してデータをダウンロードします。

ネットワーク経由でデータのダウンロードは非同期に実行する必要があります。 利点ようにされている場合は大量のデータの転送または接続が低速の場合は、ダウンロード プロセスはクライアント上の他のプロセスをブロックされません。

非同期モニカーは、ネットワーク経由でデータを非同期的にダウンロードする方法を提供します。 非同期モニカーで読み取り操作は、操作が完了されていない場合でも、すぐに返します。

たとえば、のみが 10 バイトが使用可能な読み取りは 1 K ファイルを非同期的に呼び出されます。、読み取りブロックしないが現在使用可能な 10 バイトを返します。

実装する[非同期モニカー](../mfc/asynchronous-monikers-on-the-internet.md)を使用して、`CAsyncMonikerFile`クラス。 ただし、ActiveX コントロールを使用できる、`CDataPathProperty`クラスから派生した`CAsyncMonikerFile`、非同期のコントロールのプロパティを実装するのに役立つ。

## <a name="displaying-a-control-on-a-web-page"></a>Web ページ上のコントロールを表示します。

オブジェクト タグおよび Web ページ上のコントロールを挿入するための属性の例を次に示します。

```xml
<OBJECT
  CLASSID="clsid:FC25B780-75BE-11CF-8B01-444553540000"
  CODEBASE="/ie/download/activex/iechart.ocx"
  ID=chart1
  WIDTH=400
  HEIGHT=200
  ALIGN=center
  HSPACE=0
  VSPACE=0>
  <PARAM NAME="BackColor" value="#ffffff"/>
  <PARAM NAME="ForeColor" value="#0000ff"/>
  <PARAM NAME="url" VALUE="/ie/controls/chart/mychart.txt"/>
</OBJECT>
```

## <a name="updating-an-existing-ole-control-to-use-new-activex-control-features"></a>ActiveX コントロールの新しい機能を使用する既存の OLE コントロールを更新しています

OLE コントロールは、Visual C の 4.2 より前のバージョンで作成されている場合、パフォーマンスが向上し、その機能を強化するために行える手順があります。 これらの変更の詳細については、次を参照してください。 [ActiveX コントロール。最適化](../mfc/mfc-activex-controls-optimization.md)します。

非同期のプロパティのサポートを追加する既存のコントロールには、準備完了状態プロパティを追加する必要があります、`ReadyStateChange`イベント自分でします。 コントロールのコンス トラクターは、次のように追加します。

[!code-cpp[NVC_MFCActiveXControl#8](../mfc/codesnippet/cpp/activex-controls-on-the-internet_8.cpp)]

呼び出すことによって、コードのダウンロード、準備完了状態を更新する、[中](../mfc/reference/colecontrol-class.md#internalsetreadystate)します。 呼び出すことが 1 か所`InternalSetReadyState`からは、`OnProgress`のオーバーライド`CDataPathProperty`-クラスを派生します。

## <a name="see-also"></a>関連項目

[MFC インターネット プログラミングの作業](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC インターネット プログラミングの基礎](../mfc/mfc-internet-programming-basics.md)
