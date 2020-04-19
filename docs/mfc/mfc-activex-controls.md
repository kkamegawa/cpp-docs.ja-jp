---
title: MFC ActiveX コントロール
ms.date: 11/19/2018
f1_keywords:
- MFC ActiveX Controls (MFC)
helpviewer_keywords:
- COleControl class [MFC], MFC ActiveX controls
- ActiveX controls [MFC], MFC
- containers [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], serializing
- MFC ActiveX controls [MFC], containers
- serialization [MFC], MFC ActiveX controls
- dispatch maps [MFC], for MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- events [MFC], ActiveX controls
- MFC ActiveX controls [MFC]
ms.assetid: c911fb74-3afc-4bf3-a0f5-7922b14d9a1b
ms.openlocfilehash: a1c7bb070a75f4406556817163931f0707706c40
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "69508124"
---
# <a name="mfc-activex-controls"></a>MFC ActiveX コントロール

ActiveX コントロールは、コンポーネント オブジェクト モデル (COM: Component Object Model) に基づく再利用可能なソフトウェア コンポーネントです。多岐にわたる OLE の機能をサポートしており、さまざまなソフトウェアの要件に合わせてカスタマイズできます。

>[!IMPORTANT]
> ActiveX は、新しい開発には使用しない従来のテクノロジです。 詳細については、「 [ActiveX コントロール](activex-controls.md)」を参照してください。

ActiveX コントロールは、通常の ActiveX コントロール コンテナー内と、インターネット上の WWW (World Wide Web) ページの両方で使用できるように設計されています。 ActiveX コントロールは、ここで説明するように、または[Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md)を使用して作成できます。

ActiveX コントロールは、独自のウィンドウに自らを描画し、(マウス クリックなどの) イベントに応答し、オートメーション オブジェクトに含まれているのと同様のプロパティおよびメソッドを含むインターフェイスを通じて管理することができます。

これらのコントロールは、データベース アクセス、データの監視、またはグラフの作成など、多くの用途で開発できます。 移植性以外にも、既存の OLE コンテナーとの互換性、OLE コンテナーのメニューと自らのメニューの統合など、以前の ActiveX コントロールでは使用できなかった機能が、現在の ActiveX コントロールではサポートされています。 また、ActiveX コントロールはオートメーションを完全にサポートしており、その結果、コントロールは読み取り/書き込みのプロパティや一連のメソッドを公開し、コントロール ユーザーがそれらを呼び出すことができます。

ウィンドウなしの ActiveX コントロールや、アクティブになったときのみウィンドウを作成する ActiveX コントロールを作成することもできます。 ウィンドウなしのコントロールを使用すると、アプリケーションの表示が高速化され、透明なコントロールや長方形以外のコントロールを作り出すこともできます。 また、ActiveX コントロールのプロパティを非同期で読み込むこともできます。

ActiveX コントロールは、インプロセス サーバー (通常は小さなオブジェクト) として実装され、任意の OLE コンテナー内で使用することができます。 ActiveX コントロールに対応するように設計された OLE コンテナー内で ActiveX コントロールを使用する場合のみ、ActiveX コントロールのすべての機能を利用できることに注意してください。 ActiveX コントロールをサポートするコンテナーの一覧については、「 [Activex コントロールを他のアプリケーションに移植する](../mfc/containers-for-activex-controls.md)」を参照してください。 これ以後はこのコンテナーの種類を "コントロール コンテナー" と呼びますが、これらのコンテナーはコントロールのプロパティとメソッドを使用して ActiveX コントロールを操作し、イベントの形式で ActiveX コントロールからの通知を受け取ることができます。 次の図に、この双方向のやり取りを示します。

![ActiveX コントロールコンテナーとコントロールの対話](../mfc/media/vc37221.gif "ActiveX コントロールコンテナーとコントロールの対話") <br/>
ActiveX コントロール コンテナーとウィンドウを持つ ActiveX コントロールとの対話

Activex コントロールの最適化に関する最近の情報につい[ては、「MFC activex コントロール:最適化](../mfc/mfc-activex-controls-optimization.md)。

MFC ActiveX コントロールを作成するには、「 [activex コントロールプロジェクトの作成](../mfc/reference/mfc-activex-control-wizard.md)」を参照してください。

詳細については次を参照してください:

- [ActiveX コントロール コンテナー](../mfc/activex-control-containers.md)

- [アクティブ ドキュメント](../mfc/active-documents.md)

- [ActiveX コントロールについて](/windows/win32/com/activex-controls)

- [インターネットで使用するための既存の ActiveX コントロールのアップグレード](../mfc/upgrading-an-existing-activex-control.md)

##  <a name="_core_basic_components_of_an_activex_control"></a>ActiveX コントロールの基本コンポーネント

ActiveX コントロールは複数のプログラム要素を使用して、コントロール コンテナーやユーザーとの双方向のやり取りを効率的に実行します。 これらは、クラス[COleControl](../mfc/reference/colecontrol-class.md)、一連のイベント発生関数、およびディスパッチマップです。

独自に開発するすべての ActiveX コントロール オブジェクトは、MFC 基底クラス `COleControl` から強力な機能セットを継承します。 これらの機能には、埋め込み先でのアクティブ化機能と、オートメーション ロジックが含まれています。 `COleControl` はコントロール オブジェクトに対して、MFC ウィンドウ オブジェクトと同じ機能、およびイベント発生機能を提供できます。 `COleControl`には、ウィンドウに用意されている機能の一部 (マウスキャプチャ、キーボードフォーカス、スクロール) を支援するためにコンテナーに依存している、ウィンドウ[なしのコントロール](../mfc/providing-windowless-activation.md)も用意されていますが、表示はより高速になります。

コントロール クラスは `COleControl` から派生するため、特定の条件が満たされている場合は、コントロール コンテナーに対して、イベントとも呼ばれるメッセージを送信、つまり "発生させる" 機能を継承します。 これらのイベントは、コントロール内で重要な動作が発生したときにそのことをコントロール コンテナーに通知するために使用されます。 イベントにパラメーターをアタッチして、イベントに関する追加情報をコントロール コンテナーに送信することもできます。 Activex コントロールイベントの詳細については、MFC [activex コントロールに関する記事を参照してください。イベント](../mfc/mfc-activex-controls-events.md)。

最後の要素はコントロール ユーザーに対して一連の関数 (メソッド) と属性 (プロパティ) を公開するために使用されるディスパッチ マップです。 プロパティを使用すると、コントロール コンテナーまたはコントロール ユーザーがさまざまな方法でコントロールを操作できます。 ユーザーはコントロールの外観の変更、コントロールの特定の値の変更、コントロールが維持する特定のデータへのアクセスなど、コントロールに対する要求を実行することもできます。 このインターフェイスは、コントロールの開発者によって決定され、**クラスビュー**を使用して定義されます。 Activex コントロールのメソッドとプロパティの詳細については、 [MFC activex コントロールに関する記事を参照してください。メソッド](../mfc/mfc-activex-controls-methods.md)と[プロパティ](../mfc/mfc-activex-controls-properties.md)。

##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a>Windows および ActiveX コントロールコンテナーを使用したコントロール間の相互作用

コントロール コンテナー内でコントロールを使用すると、コントロールは 2 つのメカニズムを使用して通信を行います。つまり、プロパティとメソッドを公開し、イベントを発生させます。 次の図に、これら 2 つのメカニズムを実装する方法を示します。

![ActiveX コントロールはコンテナーと通信](../mfc/media/vc37222.gif "ActiveX コントロールはコンテナーと通信") <br/>
ActiveX コントロール コンテナーと ActiveX コントロールとの通信

前の図では、コントロールが他の OLE インターフェイスを (オートメーションとイベント以外の方法で) 処理する方法も示します。

コントロールとコンテナーとのすべての通信は、`COleControl` によって実行されます。 は、コンテナーの要求の一部を処理`COleControl`するために、コントロールクラスに実装されているメンバー関数を呼び出します。 すべてのメソッドと一部のプロパティは、この方法で処理されます。 開発するコントロールが属するクラスは、`COleControl` のメンバー関数を呼び出して、コンテナーとの通信を開始することもできます。 イベントは次の方法で発生します。

##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a>ActiveX コントロールのアクティブ状態と非アクティブ状態

各コントロールには、アクティブおよび非アクティブという 2 つの基本的な状態があります。 従来、これらの状態は、コントロールがウィンドウを持つかどうかという形で判別されていました。 アクティブなコントロールはウィンドウを持ち、非アクティブなコントロールはウィンドウを持たないという分類でした。 ウィンドウなしのアクティブ状態が導入された結果、この区別はもう普遍的ではありませんが、今でも多くのコントロールに適用されます。

[ウィンドウなしのコントロール](../mfc/providing-windowless-activation.md)がアクティブになると、マウスのキャプチャ、キーボードフォーカス、スクロール、およびその他のウィンドウサービスがコンテナーから呼び出されます。 また、[非アクティブなコントロールにマウスの操作を提供](../mfc/providing-mouse-interaction-while-inactive.md)したり、ウィンドウを[作成するためにアクティブ化されるまで待機](../mfc/turning-off-the-activate-when-visible-option.md)するコントロールを作成したりすることもできます。

ウィンドウを持つコントロールがアクティブになると、コントロール コンテナー、ユーザー、および Windows との双方向のやり取りができます。 下の図では、ActiveX コントロール、コントロール コンテナー、およびオペレーティング システムの間の通信パスを示します。

![アクティブなウィンドウ ActiveX コントロールでのメッセージ処理](../mfc/media/vc37223.gif "アクティブなウィンドウ ActiveX コントロールでのメッセージ処理") <br/>
ウィンドウを持つ ActiveX コントロールがアクティブになったときの Windows メッセージの処理

##  <a name="_core_serializing_activex_elements"></a>シリアル化

永続化とも呼ばれるデータのシリアル化機能により、コントロールは自らのプロパティの値を永続ストレージに書き込むことができます。 その後、ストレージからオブジェクトの状態を読み取ることで、コントロールを再作成できます。

コントロールは、ストレージ メディアにアクセスする役割を果たさないことに注意してください。 代わりに、適切なときに使用できるように、コントロール コンテナーがストレージ メディアをコントロールに提供する役割を果たします。 シリアル化の詳細については、 [MFC ActiveX コントロールに関する記事を参照してください。シリアル](../mfc/mfc-activex-controls-serializing.md)化。 シリアル化の最適化の詳細については、「ActiveX コントロールでの[永続化と初期化の最適化](../mfc/optimizing-persistence-and-initialization.md)」を参照してください。最適化.

##  <a name="_core_installing_activex_control_classes_and_tools"></a>ActiveX コントロールクラスとツールのインストール

Visual C++ をインストールするときに、セットアップで ActiveX コントロールを選択した (既定で選択されます) 場合は、MFC ActiveX コントロール クラス、およびリテール バージョンとデバッグ バージョンの ActiveX コントロール ランタイム DLL が自動的にインストールされます。

既定では、ActiveX コントロールクラスとツールは、次のサブディレクトリにインストールされています。

- **\Common7\Tools**

   テスト コンテナー ファイル (TstCon32.exe、およびそのヘルプ ファイル) を格納します。

- **\Vc7\atlmfc\include**

   MFC を使用して ActiveX コントロールを開発するために必要なインクルード ファイルを格納します。

- **\Vc7\atlmfc\src\mfc**

   MFC 内の特定の ActiveX コントロール クラスに対応するソース コードを格納します。

- **\Vc7\atlmfc\lib**

   MFC を使用して ActiveX コントロールを開発するために必要なライブラリを格納します。

また、MFC ActiveX コントロール用のサンプルもあります。 これらのサンプルの詳細について[は、「コントロールのサンプル:MFC ベースの ActiveX コントロール](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>関連項目

[ユーザーインターフェイス要素](../mfc/user-interface-elements-mfc.md)
