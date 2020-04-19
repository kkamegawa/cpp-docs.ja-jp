---
title: インターネット上の非同期モニカー
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX controls [MFC], asynchronous
- MFC, asynchronous monikers
- asynchronous monikers [MFC]
- Web applications [MFC], asynchronous
- downloading Internet resources and asynchronous monikers
- optimization [MFC], asynchronous downloading across Internet
- Internet [MFC], asynchronous downloading
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
ms.openlocfilehash: e7a7ea51bca134e965747db8aac7f8a62822c9eb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165841"
---
# <a name="asynchronous-monikers-on-the-internet"></a>インターネット上の非同期モニカー

インターネットには、その低速のネットワーク アクセスのための新しい方法でアプリケーションの設計が必要です。 アプリケーションでは、ユーザー インターフェイスの停止を回避するには、非同期的にネットワーク アクセスを実行する必要があります。 MFC クラス[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)ファイルをダウンロードするための非同期サポートを提供します。

非同期モニカーは、インターネット経由で非同期的にダウンロードし、ビットマップなどのラージ オブジェクトと VRML オブジェクトのプログレッシブのレンダリングを提供する COM アプリケーションを拡張できます。 非同期モニカーには、ActiveX コントロールのプロパティまたはユーザー インターフェイスの応答をブロックすることがなくダウンロードにインターネット上のファイルが有効にします。

## <a name="advantages-of-asynchronous-monikers"></a>非同期モニカーの利点

非同期モニカーを使用することができます。

- ブロックすることがなく、コード ファイルとファイルをダウンロードします。

- ブロックすることがなく、ActiveX コントロールのプロパティをダウンロードします。

- ダウンロードの進行状況の通知を受信します。

- 進行状況と状態情報を追跡します。

- 進行状況に関するユーザー状態情報を提供します。

- いつでもダウンロードをキャンセルできます。

## <a name="mfc-classes-for-asynchronous-monikers"></a>非同期モニカー用の MFC クラス

[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)から派生[CMonikerFile](../mfc/reference/cmonikerfile-class.md)、さらにから派生する[COleStreamFile](../mfc/reference/colestreamfile-class.md)します。 A`COleStreamFile`するデータのストリームは、オブジェクトが表す`CMonikerFile`オブジェクトで使用、 `IMoniker` 、データを取得して、`CAsyncMonikerFile`オブジェクトは、これを非同期的には。

非同期モニカーは、ファイル転送中に、応答性の高いユーザー インターフェイスを提供するインターネット対応のアプリケーションと ActiveX コントロールで主に使用されます。 これの典型的な例の使用は、 [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md) ActiveX コントロールの非同期のプロパティを提供します。

## <a name="mfc-classes-for-data-paths-in-activex-controls"></a>ActiveX コントロールのデータ パスの MFC クラス

MFC クラス`CDataPathProperty`と[CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)非同期的に読み込むことができる ActiveX コントロールのプロパティを実装します。 同期の開始後は、非同期のプロパティが読み込まれます。 非同期の ActiveX コントロールは、時間のかかるプロパティ exchange の処理中に新しいデータの可用性を示すコールバックを繰り返し呼び出します。

`CDataPathProperty` は、`CAsyncMonikerFile` から派生しています。 `CCachedDataPathProperty` は、`CDataPathProperty` から派生しています。 ActiveX コントロールで非同期のプロパティを実装するには、派生クラスを`CDataPathProperty`または`CCachedDataPathProperty`、オーバーライドと[OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable)とその他の通知の受信を希望します。

#### <a name="to-download-a-file-using-asynchronous-monikers"></a>非同期モニカーを使用してファイルをダウンロードするには

1. 派生したクラスを宣言[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)します。

1. オーバーライド[OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable)データを表示します。

1. などの他のメンバー関数をオーバーライド[OnProgress](../mfc/reference/casyncmonikerfile-class.md#onprogress)、 [OnStartBinding](../mfc/reference/casyncmonikerfile-class.md#onstartbinding)、および[は](../mfc/reference/casyncmonikerfile-class.md#onstopbinding)します。

1. このクラスのインスタンスを宣言し、Url を開くために使用します。

ActiveX コントロールにおける非同期的にダウンロード方法の詳細については、次を参照してください。[インターネット上の ActiveX コントロール](../mfc/activex-controls-on-the-internet.md)します。

## <a name="see-also"></a>関連項目

[MFC インターネット プログラミングの作業](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC インターネット プログラミングの基礎](../mfc/mfc-internet-programming-basics.md)
