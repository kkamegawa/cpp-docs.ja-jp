---
title: メニューとリソース:サーバーの変更点
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
helpviewer_keywords:
- OLE visual editing servers [MFC]
- accelerator tables [MFC], server applications
- visual editing [MFC], application menus and resources
- server applications [MFC], accelerator table
- string tables [MFC], visual editing applications
- servers [MFC], menu additions
- resources [MFC], server applications
- OLE server applications [MFC], menus and resources
- string editing [MFC], visual editing applications
- IDP_OLE_INIT_FAILED macro [MFC]
- server applications [MFC], OLE menus and resources
- OLE initialization failure [MFC]
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
ms.openlocfilehash: 85c7b6059a868e93c6c6a7ebbd7b08dac3233612
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62225424"
---
# <a name="menus-and-resources-server-additions"></a>メニューとリソース:サーバーの変更点

この記事では、メニューとビジュアル編集サーバー (コンポーネント) アプリケーションでは、その他のリソースをする必要がある変更について説明します。 3 つのモードのいずれかで開始することができるため、サーバー アプリケーションは、メニュー構造とその他のリソースに多くの追加が必要です。 埋め込まれた、または場所にスタンドアロンです。 」の説明に従って、[メニューとリソース (OLE)](../mfc/menus-and-resources-ole.md)に関する記事で、メニューの 4 つのセットの最大値があります。 ミニサーバーに 3 つのみが使用中に、MDI フル サーバー アプリケーションは、4 つすべてが使用されます。 アプリケーション ウィザード メニューのレイアウトをサーバーの種類に必要な作成されます。 いくつかカスタマイズ必要があります。

アプリケーション ウィザードを使用しない場合 HIERSVR を確認したい場合があります。RC では、MFC のサンプル アプリケーションについては、リソース スクリプト[HIERSVR](../overview/visual-cpp-samples.md)、これらの変更を実装する方法を確認します。

この記事で説明したトピックは次のとおりです。

- [サーバーのメニューの追加](#_core_server_menu_additions)

- [アクセラレータ テーブルの変更点](#_core_server_application_accelerator_table_additions)

- [文字列テーブルの変更点](../mfc/menus-and-resources-container-additions.md)

- [ミニサーバーの変更点](#_core_mini.2d.server_additions)

##  <a name="_core_server_menu_additions"></a> サーバーのメニューの追加

OLE ビジュアル編集をサポートするために追加されたメニュー リソース (コンポーネント) のサーバー アプリケーションが必要です。 スタンドアロン モードでアプリケーションを実行するときに使用するメニューを変更する必要はありませんが、アプリケーションを構築する前に、2 つの新しいメニュー リソースを追加する必要があります。 インプレース アクティブ化と完全にオープンされているサーバーをサポートする 1 つをサポートするために 1 つ。 両方のメニュー リソースは、アプリケーション、およびミニサーバー アプリケーションによって使用されます。

- インプレース アクティブ化をサポートするには、スタンドアロン モードで実行するときに使用するメニュー リソースに非常に類似したメニュー リソースを作成する必要があります。 このメニューでの違いは、ファイルとウィンドウの項目 (および、アプリケーションとデータを処理する他のメニュー項目) がないことです。 コンテナー アプリケーションでは、これらのメニュー項目を提供します。 詳細についてと、このメニューのマージ方法の例では、記事を参照してください。[メニューとリソース。メニューのマージ](../mfc/menus-and-resources-menu-merging.md)します。

- 完全なオープン ライセンス認証をサポートするには、スタンドアロン モードで実行するとメニュー リソースを使用するとほぼ同じメニュー リソースを作成する必要があります。 このメニュー リソースに対する唯一の変更は、複合ドキュメントに埋め込まれている項目で、サーバーが動作しているという事実を反映するようにいくつかの項目を改めことです。

この記事に記載の変更を加え、リソース ファイルを AFXOLESV を含める必要があります。RC では、Microsoft Foundation Class ライブラリの実装に必要です。 このファイルは、定義してサブディレクトリです。

##  <a name="_core_server_application_accelerator_table_additions"></a> サーバー アプリケーションのアクセラレータ テーブルの追加

2 つの新しいアクセラレータ テーブル リソースは、サーバー アプリケーションに追加する必要があります。前述の新しいメニュー リソースに直接対応します。 最初のアクセラレータ テーブルは、インプレース アクティブ化されると、サーバー アプリケーションで使用されます。 それらに関連付けられているファイルとウィンドウ メニュー点を除いて、ビューのアクセラレータ テーブル内のすべてのエントリで構成されます。

2 番目のテーブルは、ほぼビューのアクセラレータ テーブルの正確なコピーです。 説明したメニューで行われた変更を書き換えて[Server メニュー Additions](#_core_server_menu_additions)。

これらのアクセラレータ テーブルの変更など、hiersvr IDR_MAINFRAME で IDR_HIERSVRTYPE_SRVR_IP と IDR_HIERSVRTYPE_SRVR_EMB アクセラレータ テーブルを比較します。MFC OLE サンプルに含まれる RC ファイル[HIERSVR](../overview/visual-cpp-samples.md)します。 ファイルおよびウィンドウのアクセラレータは、インプレース テーブルから不足していると、それらの正確なコピーは、埋め込みテーブル。

##  <a name="_core_string_table_additions_for_server_applications"></a> サーバー アプリケーションの文字列テーブルの変更点

1 つのみの文字列テーブルの追加は、サーバー アプリケーションで必要: OLE の初期化が失敗したことを示す文字列。 たとえば、アプリケーション ウィザードで生成する、文字列テーブル エントリを示します。

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE の初期化に失敗しました。 OLE ライブラリの正しいバージョンがあることを確認します。|

##  <a name="_core_mini.2d.server_additions"></a> ミニサーバーの変更点

同じ追加機能を上に示したものとして miniservers の適用の全サーバー。 ミニサーバーは、スタンドアロン モードで実行することはできません、ため、メイン メニューがかなり小さくなります。 アプリケーション ウィザードによって作成されたメイン メニューにのみ、ファイル メニューの終了の項目のみを含むしようとします。 埋め込みおよびインプレース メニューおよび miniservers のアクセラレータは、完全なサーバーの場合と同じです。

## <a name="see-also"></a>関連項目

[メニューとリソース (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[メニューとリソース: メニューの結合](../mfc/menus-and-resources-menu-merging.md)
