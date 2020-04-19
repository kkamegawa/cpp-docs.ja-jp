---
title: OLE コントロール クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
ms.openlocfilehash: 86470c3e3e66d6aee2ce532570cea096641d2c1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186089"
---
# <a name="ole-control-classes"></a>OLE コントロール クラス

これらは、OLE コントロールを作成するときに使用するプライマリ クラスです。 `COleControlModule` OLE コントロール モジュールのクラスは似ています、 [CWinApp](../mfc/reference/cwinapp-class.md)アプリケーション内のクラス。 各モジュールは 1 つまたは複数の OLE コントロール。これらのコントロールがによって表される`COleControl`オブジェクト。 これらのコントロールを使用して、コンテナーと通信`CConnectionPoint`オブジェクト。

`CPictureHolder`と`CFontHolder`クラスは、画像やフォントなどの COM インターフェイスをカプセル化中に、`COlePropertyPage`と`CPropExchange`クラスを使用して、プロパティ ページとコントロールのプロパティの永続化を実装できます。

[COleControlModule](../mfc/reference/colecontrolmodule-class.md)<br/>
置換、 `CWinApp` OLE コントロール モジュールのクラス。 派生、 `COleControlModule` OLE コントロール モジュール オブジェクトを開発するクラス。 OLE コントロールのモジュールを初期化するために、メンバー関数を提供します。

[COleControl](../mfc/reference/colecontrol-class.md)<br/>
派生、 `COleControl` OLE コントロールを開発するクラス。 派生した`CWnd`、このクラスは、Windows のウィンドウ オブジェクトのすべての機能とイベントの発生からメソッドとプロパティをサポートする機能などの追加 OLE 固有の機能を継承します。

[CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)<br/>
`CConnectionPoint`クラスは、特殊な種類の接続ポイントと呼ばれる他の OLE オブジェクトとの通信に使用されるインターフェイスを定義します。 接続ポイントは、イベントを発生させるなどの他のオブジェクトに対するアクションを開始して、変更通知が送信インターフェイスを実装します。

[CPictureHolder](../mfc/reference/cpictureholder-class.md)<br/>
Windows 画像オブジェクトの機能をカプセル化し、 `IPicture` COM インターフェイス; OLE コントロールのカスタム Picture プロパティを実装するために使用します。

[CFontHolder](../mfc/reference/cfontholder-class.md)<br/>
Windows のフォント オブジェクトの機能をカプセル化し、 `IFont` COM インターフェイス; OLE コントロールのストック フォント プロパティを実装するために使用します。

[COlePropertyPage](../mfc/reference/colepropertypage-class.md)<br/>
ダイアログ ボックスのようなグラフィカル インターフェイスで制御する OLE のプロパティを表示します。

[CPropExchange](../mfc/reference/cpropexchange-class.md)<br/>
OLE コントロールのプロパティの永続化の実装をサポートしています。 類似しています[CDataExchange](../mfc/reference/cdataexchange-class.md)のダイアログ ボックス。

[CMonikerFile](../mfc/reference/cmonikerfile-class.md)<br/>
モニカー、または、モニカーに行うことができますを文字列形式を受け取り、モニカーは名前のストリームに同期的にバインドします。

[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)<br/>
同じように動作`CMonikerFile`。 ただし、モニカーは名前のストリームに、モニカーを非同期的にバインドにします。

[CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)<br/>
非同期で読み込める OLE コントロール プロパティを実装します。

[CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)<br/>
非同期で転送し、メモリ ファイルにキャッシュする OLE コントロール プロパティを実装します。

[COleCmdUI](../mfc/reference/colecmdui-class.md)<br/>
により、作業中の文書 (という名前、開く、印刷、具合) などのコンテナーのユーザー インターフェイスで発生するコマンドを受信でき、アクティブなドキュメントのユーザー インターフェイスで発生するコマンドを受信するためのコンテナー。

[COleSafeArray](../mfc/reference/colesafearray-class.md)<br/>
任意の型と次元の配列で機能します。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
