---
title: メニューとリソース:コンテナーの変更点
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
helpviewer_keywords:
- application accelerator table [MFC]
- VK_ESCAPE key [MFC]
- IDP_FAILED_TO_CREATE macro [MFC]
- visual editing, application menus and resources
- OLE containers [MFC], menus and resources
- accelerator tables [MFC], container applications
- IDP_OLE_INIT_FAILED macro [MFC]
- CONTAIN tutorial [MFC]
- Links menu item [MFC]
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
ms.openlocfilehash: b1a74fef743592d3d052226dac926fc7ddc58578
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363467"
---
# <a name="menus-and-resources-container-additions"></a>メニューとリソース:コンテナーの変更点

この記事では、メニューとビジュアル編集コンテナー アプリケーションでは、その他のリソースをする必要がある変更について説明します。

コンテナーのアプリケーションで 2 つの種類の変更が必要になる: OLE ビジュアル編集し、インプレース アクティブ化に使用される新しいリソースの追加をサポートするために既存のリソースに変更します。 コンテナー アプリケーションを作成するアプリケーション ウィザードを使用する場合は、これらの手順は、実行されますが、いくつかカスタマイズする必要があります。

アプリケーション ウィザードを使用しない場合 OCLIENT を確認したい場合があります。RC では、リソース スクリプトの OCLIENT サンプル アプリケーションのこれらの変更を実装する方法を確認します。 MFC OLE サンプルを参照して[OCLIENT](../overview/visual-cpp-samples.md)します。

この記事で説明したトピックは次のとおりです。

- [コンテナー メニューの追加](#_core_container_menu_additions)

- [アクセラレータ テーブルの変更点](#_core_container_application_accelerator_table_additions)

- [文字列テーブルの変更点](#_core_string_table_additions_for_container_applications)

##  <a name="_core_container_menu_additions"></a> コンテナー メニューの追加

[編集] メニューには、次の項目を追加する必要があります。

|アイテム|目的|
|----------|-------------|
|**新しいオブジェクトを挿入します。**|ドキュメントにリンクまたは埋め込み項目を挿入する OLE の [オブジェクトの挿入] ダイアログ ボックスが開きます。|
|**貼り付けのリンク**|アイテムへのリンクをクリップボードに、ドキュメントに貼り付けます。|
|**OLE の動詞**|選択した項目の主動詞を呼び出します。 選択した項目の主動詞を反映するようにこのメニュー項目の変更のテキスト。|
|**Links**|既存のリンクされた項目を変更する OLE の [リンクの編集] ダイアログ ボックスが開きます。|

この記事に記載の変更、に加えて、ソース ファイルは AFXOLECL を含める必要があります。RC では、Microsoft Foundation Class ライブラリの実装に必要です。 新規オブジェクトの挿入は、必要な唯一のメニューに追加します。 その他の項目を追加することができますが、ここに示したものは最も一般的です。

含まれている項目のインプレース アクティブ化をサポートする場合は、コンテナー アプリケーションの新しいメニューを作成する必要があります。 このメニューは、同じファイル メニューおよびウィンドウのショートカット メニューを開いているファイルがそれらの間に配置する 2 つの区切り記号がある場合に使用で構成されます。 これらの区切り文字を使用して、サーバー (コンポーネント) アイテム (アプリケーション) がインプレース アクティブ化されるときに、そのメニューを配置する場所を指定します。 このメニューのマージ方法の詳細については、次を参照してください。[メニューとリソース。メニューのマージ](../mfc/menus-and-resources-menu-merging.md)します。

##  <a name="_core_container_application_accelerator_table_additions"></a> コンテナー アプリケーションのアクセラレータ テーブルの追加

コンテナー アプリケーションのアクセラレータ テーブル リソースを少し変更は、インプレース アクティブ化をサポートしている場合に必要です。 最初の変更により、ユーザーが、インプレース編集モードをキャンセル (ESC) は、esc キーを押します。 メインのアクセラレータ テーブルには、次のエントリを追加します。

|ID|キー|型|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

2 番目の変更では、インプレース アクティブ化用に作成された新しいメニュー リソースに対応する新しいアクセラレータ テーブルを作成します。 このテーブルには、上記の VK_ESCAPE エントリに加えてファイルとウィンドウのメニューのエントリがあります。 次の例は、MFC のサンプルでは、インプレース アクティブ化用に作成されたアクセラレータ テーブル[コンテナー](../overview/visual-cpp-samples.md):

|ID|キー|型|
|--------|---------|----------|
|ID_FILE_NEW|Ctrl + N|**VIRTKEY**|
|ID_FILE_OPEN|Ctrl + O|**VIRTKEY**|
|ID_FILE_SAVE|Ctrl + S|**VIRTKEY**|
|ID_FILE_PRINT|Ctrl + P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|SHIFT + VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

##  <a name="_core_string_table_additions_for_container_applications"></a> コンテナー アプリケーションの文字列テーブルの変更点

コンテナー アプリケーションの文字列テーブルへの変更の大部分で説明されている他のメニュー項目に対応[コンテナー メニューの追加](#_core_container_menu_additions)します。 各メニュー項目が表示されるときに、ステータス バーに表示されるテキストを指定します。 例として、次に、アプリケーション ウィザードで生成ストリング テーブルのエントリを示します。

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE の初期化に失敗しました。 OLE ライブラリの正しいバージョンがあることを確認します。|
|IDP_FAILED_TO_CREATE|オブジェクトを作成できませんでした。 オブジェクトがシステム レジストリに登録されていることを確認します。|

## <a name="see-also"></a>関連項目

[メニューとリソース (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[メニューとリソース: サーバーの変更点](../mfc/menus-and-resources-server-additions.md)
