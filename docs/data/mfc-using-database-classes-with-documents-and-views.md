---
title: MFC:ドキュメントとビューを用いたデータベース クラス
ms.date: 11/04/2016
helpviewer_keywords:
- documents [C++], database applications
- recordsets [C++], documents and views
- CRecordView class, using in database forms
- views [C++], database applications
- forms [C++], database applications
- record views [C++], form-based applications
- document/view architecture [C++], in databases
- database applications [C++], forms
- database classes [C++], MFC
- ODBC recordsets [C++], documents and views
- ODBC [C++], forms
ms.assetid: 83979974-fc63-46ac-b162-e8403a572e2c
ms.openlocfilehash: 78765d17b52889123f13c492699230834decba66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182900"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC:ドキュメントとビューを用いたデータベース クラス

ドキュメント/ビュー アーキテクチャの有無は、MFC データベース クラスを使用することができます。 このトピックでは、ドキュメントとビューの操作を強調します。 これを説明します。

- [フォーム ベースのアプリケーションの記述方法](#_core_writing_a_form.2d.based_application)を使用して、`CRecordView`として、ドキュメントのメイン ビューのオブジェクト。

- [ドキュメントとビューでのレコード セット オブジェクトを使用する方法](#_core_using_recordsets_in_documents_and_views)します。

- [他の考慮事項](#_core_other_factors)します。

代替方法については、次を参照してください[MFC:。ドキュメントとビューを用いないデータベース クラスを使用して](../data/mfc-using-database-classes-without-documents-and-views.md)します。

##  <a name="_core_writing_a_form.2d.based_application"></a> フォーム ベースのアプリケーションの作成

多くのデータ アクセス アプリケーションは、フォームに基づいています。 ユーザー インターフェイスは、コントロールをユーザーを調べ、入力すると、または編集データを含む形式です。 クラスを使用するために、アプリケーションのフォーム ベースの`CRecordView`します。 MFC アプリケーション ウィザードを実行し、選択**ODBC**でクライアントの種類、**データベース サポート** ページで、プロジェクトを使用して`CRecordView`ビュー クラスの。

レコード ビューの各オブジェクトがへのポインターを格納するフォーム ベースのアプリケーションで、`CRecordset`オブジェクト。 フレームワークのレコード フィールド エクス (チェンジ RFX) メカニズムでは、レコード セットと、データ ソース間でデータを交換します。 ダイアログ データでは、レコード セット オブジェクトのフィールド データ メンバーと、フォーム上のコントロールの間 (DDX) メカニズム交換データを交換します。 `CRecordView` 既定コマンド ハンドラー関数を提供します、フォームのレコード間を移動します。

アプリケーション ウィザードを使用して、フォーム ベースのアプリケーションを作成するを参照してください。[フォーム ベースの MFC アプリケーションの作成](../mfc/reference/creating-a-forms-based-mfc-application.md)と[データベースのサポート、MFC アプリケーション ウィザード](../mfc/reference/database-support-mfc-application-wizard.md)します。

フォームの詳細については、次を参照してください。[レコード ビュー](../data/record-views-mfc-data-access.md)します。

##  <a name="_core_using_recordsets_in_documents_and_views"></a> ドキュメントとビュー内のレコード セットを使用します。

多くの単純なフォーム ベースのアプリケーションでは、ドキュメントは必要ありません。 アプリケーションより複雑なデータベースのプロキシとして、ドキュメントを使用する可能性がありますが場合に、格納する、`CDatabase`データ ソースに接続するオブジェクト。 通常、フォーム ベースのアプリケーションは、ビューで、レコード セット オブジェクトへのポインターを格納します。 その他のデータベース アプリケーションは、レコード セットを格納および`CDatabase`ドキュメント内のオブジェクト。 データベース アプリケーションでドキュメントの使用例を次に示します。

- ローカル コンテキストのレコード セットにアクセスする場合は、作成、`CRecordset`必要に応じて、ドキュメントまたはビューのメンバー関数でローカル オブジェクトです。

   関数のローカル変数として、レコード セット オブジェクトを宣言します。 フレームワークを作成し、一時的なを開くと、コンス トラクターに NULL を渡す`CDatabase`オブジェクト。 代わりへのポインターを渡す、`CDatabase`オブジェクト。 関数内でレコード セットを使用し、関数が終了したときに自動的に破棄されるようにします。

   レコード セットのコンス トラクターに NULL を渡すと、ときに、framework は、レコード セットによって返される情報`GetDefaultConnect`メンバー関数を作成する、`CDatabase`オブジェクトを開きます。 ウィザード実装`GetDefaultConnect`できます。

- レコード セットをドキュメントの有効期間中にアクセスする場合は、1 つまたは複数を埋め込む`CRecordset`ドキュメント内のオブジェクト。

   ドキュメントを初期化するときに、または必要に応じて、レコード セット オブジェクトを構築します。 既に存在する場合、または構築がまだ存在しない場合は、レコード セットを開き、レコード セットにポインターを返す関数を記述する場合があります。 閉じる、削除、および、必要に応じて、レコード セットを再作成または呼び出すその`Requery`レコードを更新するメンバー関数。

- ドキュメントの有効期間中に、データ ソースにアクセスする場合は、埋め込み、`CDatabase`オブジェクトまたはへのポインターを格納、`CDatabase`内のオブジェクト。

   `CDatabase`オブジェクトは、データ ソースへの接続を管理します。 オブジェクトは、ドキュメントの構築時に自動的に構築し、呼び出すことがその`Open`メンバー関数は、ドキュメントを初期化するときにします。 ドキュメントへのポインターを渡すメンバー関数のドキュメント内のレコード セット オブジェクトを構築する際に`CDatabase`オブジェクト。 これにより、各レコード セットがそのデータ ソースと関連付けられます。 データベース オブジェクトは、ドキュメントを閉じるときに、通常は破棄されます。 レコード セット オブジェクトは、関数のスコープを終了するときに通常は破棄されます。

##  <a name="_core_other_factors"></a> その他の要因

フォーム ベースのアプリケーションが含まれていないフレームワークのドキュメントのシリアル化機構を使用して、削除、無効にする、または置換をする可能性があります、**新規**と**オープン**コマンド、 **ファイル**メニュー。 記事をご覧ください[シリアル化します。シリアル化とデータベースの入力/出力](../mfc/serialization-serialization-vs-database-input-output.md)します。

することがありますもフレームワークがサポートする多くのユーザー インターフェイス可能性を使用します。 たとえば、複数を使用できます`CRecordView`複数ドキュメント インターフェイス (MDI) 子ウィンドウは、という具合分割ウィンドウ内のオブジェクトが異なる複数のレコード セットを開きます。

ビュー内のあらゆるものの印刷を実装する、フォーム実装があるかどうか`CRecordView`またはその他。 派生したクラスとして`CFormView`、`CRecordView`印刷するには、サポートされていませんをオーバーライドできます、`OnPrint`印刷を許可するメンバー関数。 詳細については、クラスを参照してください。 [CFormView](../mfc/reference/cformview-class.md)します。

ドキュメントとビューをまったく使用しない可能性があります。 その場合を参照してください[MFC:ドキュメントとビューを用いないデータベース クラスを使用して](../data/mfc-using-database-classes-without-documents-and-views.md)します。

## <a name="see-also"></a>関連項目

[MFC データベース クラス](../data/mfc-database-classes-odbc-and-dao.md)