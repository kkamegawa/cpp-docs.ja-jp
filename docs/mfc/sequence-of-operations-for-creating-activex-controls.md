---
title: ActiveX コントロールの作成手順
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
- sequence [MFC], for creating ActiveX controls
- OLE controls [MFC], MFC
- sequence [MFC]
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
ms.openlocfilehash: 020c044cc0b3b96df102a5ab6625c945f1033f67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308434"
---
# <a name="sequence-of-operations-for-creating-activex-controls"></a>ActiveX コントロールの作成手順

次の表は、(以前の OLE コントロール) の ActiveX コントロールを作成することで、役割、およびフレームワークの役割を示します。

### <a name="creating-activex-controls"></a>ActiveX コントロールを作成します。

|タスク|そうですよね|フレームワークを動作します。|
|----------|------------|------------------------|
|ActiveX コントロール フレームワークを作成します。|コントロールを作成するには、MFC ActiveX コントロール ウィザードを実行します。 [オプション] ページで、目的のオプションを指定します。 オプションには、プロジェクト、ライセンス、サブクラス化、および、バージョン情報ボックス メソッドで、コントロールの名前と型が含まれます。|MFC ActiveX コントロール ウィザード、アプリケーション、コントロール、およびプロパティ ページまたはページのソース ファイルを含む、基本的な機能を持つ ActiveX コントロールのファイルを作成しますリソース ファイル。は、プロジェクト ファイル仕様に合わせてすべて、他のユーザー。|
|独自のコード行を追加することがなく、コントロールと、ActiveX コントロール ウィザードが提供するして参照してください。|ActiveX コントロールをビルドし、Internet Explorer を使用してテストまたは[TSTCON サンプル](../overview/visual-cpp-samples.md)します。|実行中のコントロールには、サイズ変更し、移動する機能があります。 **についてボックス**呼び出すことのできるメソッド (選択) 場合。|
|コントロールのプロパティとメソッドを実装します。|コントロールのデータへの公開されているインターフェイスを提供するメンバー関数を追加することで、コントロール固有のメソッドとプロパティを実装します。 データ構造を保持して決定するときにイベントを発生させるイベント ハンドラーを使用、するメンバー変数を追加します。|フレームワークでは、コントロールのイベント、プロパティ、メソッド、プロパティとメソッドの実装方法に焦点を離れることをサポートするためのマップは既に定義します。 既定のプロパティ ページが表示され、既定のバージョン情報ボックス メソッドを提供します。|
|コントロールのプロパティ ページまたはページを構築します。|コントロールのプロパティ ページのインターフェイスを視覚的に編集するのにには、Visual C リソース エディターを使用します。<br /><br />-追加のプロパティ ページを作成します。<br />-作成し、ビットマップ、アイコン、およびカーソルを編集します。<br /><br /> ダイアログ エディターで、プロパティ ページをテストすることもできます。|MFC アプリケーション ウィザードによって作成された既定のリソース ファイルでは、必要なリソースを多数提供します。 Visual C では、既存のリソースを編集し、簡単かつ視覚的には、新しいリソースを追加することができます。|
|コントロールのイベント、メソッド、およびプロパティをテストします。|コントロールを再構築し、テスト コンテナーを使用して、ハンドラーが正しく動作をテストします。|コントロールのメソッドを呼び出すし、プロパティ ページのインターフェイス、またはテスト コンテナーを通じてそのプロパティを操作できます。 さらに、コントロールから発生したイベントの追跡およびコントロールのコンテナーで受信した通知をテスト コンテナーを使用します。|

## <a name="see-also"></a>関連項目

[フレームワークを使ったアプリケーションの作成](../mfc/building-on-the-framework.md)<br/>
[MFC アプリケーションの作成手順](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[OLE アプリケーションの作成手順](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[データベース アプリケーションの作成手順](../mfc/sequence-of-operations-for-creating-database-applications.md)
