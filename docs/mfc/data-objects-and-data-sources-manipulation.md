---
title: データ オブジェクトとデータ ソース:操作
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], manipulating
- data sources [MFC], data operations
- data sources [MFC], inserting data
- Clipboard [MFC], determining available formats
- OLE [MFC], data objects
- Clipboard [MFC], passing format information
- data sources [MFC], determining available formats
- delayed rendering [MFC]
- OLE [MFC], data sources
ms.assetid: f7f27e77-bb5d-4131-b819-d71bf929ebaf
ms.openlocfilehash: 81dfe911866c4d1ba1720ee2c9854076c499f0a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241550"
---
# <a name="data-objects-and-data-sources-manipulation"></a>データ オブジェクトとデータ ソース:操作

データ オブジェクトまたはデータ ソースが作成された後は、さまざまなデータの挿入とデータが、形式を列挙するデータの削除などの一般的な操作を実行できます。 この記事では、最も一般的な操作を完了するために必要な手法について説明します。 ここでは、次の内容について説明します。

- [データ ソースにデータを挿入](#_core_inserting_data_into_a_data_source)

- [データ オブジェクトで使用できる形式を決定します。](#_core_determining_the_formats_available_in_a_data_object)

- [データ オブジェクトからのデータの取得](#_core_retrieving_data_from_a_data_object)

##  <a name="_core_inserting_data_into_a_data_source"></a> データ ソースにデータを挿入

データ ソースにデータを挿入する方法でデータがすぐに提供されているかどうかによって異なります。 またはが指定されて、オンデマンドで、どのメディアにします。 可能性は次のとおりです。

### <a name="supplying-data-immediately-immediate-rendering"></a>データをすぐに (直接レンダリング) を指定します。

- 呼び出す`COleDataSource::CacheGlobalData`データを指定しているすべてのクリップボード形式の繰り返しです。 使用するには、クリップボードの形式を渡すデータを格納しているメモリを識別するハンドルと、オプションで、 **FORMATETC**データを記述する構造体。

     - または -

- 直接操作する場合**STGMEDIUM**構造体を呼び出す`COleDataSource::CacheData`の代わりに`COleDataSource::CacheGlobalData`で上記のオプション。

### <a name="supplying-data-on-demand-delayed-rendering"></a>(遅延レンダリング) オンデマンドでデータを提供します。

これは、高度なトピックです。

- 呼び出す`COleDataSource::DelayRenderData`データを指定しているすべてのクリップボード形式の繰り返しです。 使用するクリップボード形式を渡すと、オプションで、 **FORMATETC**データを記述する構造体。 データが要求されたときに、フレームワークは呼び出します`COleDataSource::OnRenderData`、オーバーライドする必要があります。

     - または -

- 使用する場合、 `CFile` 、データを入力するオブジェクトを呼び出す`COleDataSource::DelayRenderFileData`の代わりに`COleDataSource::DelayRenderData`前記のオプションでします。 データが要求されたときに、フレームワークは呼び出します`COleDataSource::OnRenderFileData`、オーバーライドする必要があります。

##  <a name="_core_determining_the_formats_available_in_a_data_object"></a> データ オブジェクトで使用できる形式を決定します。

アプリケーションには、ユーザーにデータを貼り付けることができるように、処理できるクリップボードの形式があるかどうかを把握する必要があります。 これを行うには、アプリケーションは、次の操作を行う必要があります。

1. 作成、`COleDataObject`オブジェクトと**FORMATETC**構造体。

1. データ オブジェクトの`AttachClipboard`にデータ オブジェクトをクリップボードのデータに関連付けるメンバー関数。

1. 次のいずれかの操作を行います。

   - データ オブジェクトの`IsDataAvailable`メンバー関数は 1 つだけを使用する必要があるか 2 つの書式設定する必要があります。 クリップボードのデータが、アプリケーションよりもはるかに多くの形式をサポートしている場合の時間の節約は、このします。

         -or-

   - データ オブジェクトの`BeginEnumFormats`メンバー関数は、クリップボードで使用できる形式の列挙を開始します。 呼び出して`GetNextFormat`クリップボードを返すまで、形式、アプリケーションがサポートまたはないその他の形式があります。

使用する場合**ON_UPDATE_COMMAND_UI**、貼り付け、および [編集] メニュー項目を貼り付けを有効にできます。 これを行うには、いずれかを呼び出す`CMenu::EnableMenuItem`または`CCmdUI::Enable`します。 どのようなコンテナーの詳細についてはアプリケーションする必要があります メニュー項目でし、を参照してください[メニューとリソース。コンテナーの変更点](../mfc/menus-and-resources-container-additions.md)します。

##  <a name="_core_retrieving_data_from_a_data_object"></a> データ オブジェクトからのデータの取得

データ形式を決めたら、残っているは、データ オブジェクトから、データを取得します。 これを行うには、ユーザーは、データを格納する場所を決定し、アプリケーションが適切な関数を呼び出します。 次のメディアのいずれかで使用可能なデータになります。

|Medium|関数を呼び出す|
|------------|----------------------|
|グローバル メモリ (`HGLOBAL`)|`COleDataObject::GetGlobalData`|
|ファイル (`CFile`)|`COleDataObject::GetFileData`|
|**STGMEDIUM**構造 (`IStorage`)|`COleDataObject::GetData`|

一般的には、メディアでのクリップボード形式と共に指定されます。 たとえば、 **CF_EMBEDDEDSTRUCT**オブジェクトは常に、`IStorage`を必要とする中、 **STGMEDIUM**構造体。 そのため、用途`GetData`受け入れることができるこれらの関数の 1 つだけのため、 **STGMEDIUM**構造体。

クリップボード形式がある場合、`IStream`または`HGLOBAL`フレームワークを提供できます、中、`CFile`データを参照するポインター。 アプリケーションは、ファイルからデータをインポートする場合と同じ方法で多くのデータを取得するために読み取るファイルを使用できます。 基本的には、これは、クライアント側のインターフェイスを`OnRenderData`と`OnRenderFileData`ルーチン、データ ソース。

ユーザーは、ドキュメントにデータの挿入と同様、同じ形式でその他のデータのようになりましたことができます。

### <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ドラッグ アンド ドロップ](../mfc/drag-and-drop-ole.md)

- [クリップボード](../mfc/clipboard.md)

## <a name="see-also"></a>関連項目

[データ オブジェクトとデータ ソース (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject クラス](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource クラス](../mfc/reference/coledatasource-class.md)
