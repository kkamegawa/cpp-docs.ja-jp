---
title: ドキュメント/ビュー アーキテクチャの代替手段
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
ms.openlocfilehash: 98bb4de2f6d1a43fc1958a0fcbaafa1ac0af82a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394716"
---
# <a name="alternatives-to-the-documentview-architecture"></a>ドキュメント/ビュー アーキテクチャの代替手段

MFC アプリケーションは通常、情報、ファイル形式、およびユーザーへのデータの視覚的表現を管理するのに、ドキュメント/ビュー アーキテクチャを使用します。 デスクトップ アプリケーションのほとんどは、ドキュメント/ビュー アーキテクチャは、適切かつ効率的なアプリケーション アーキテクチャです。 このアーキテクチャは、表示から、ほとんどの場合は、データを分離、アプリケーションを簡素化および冗長なコードを削減します。

ただし、ドキュメント/ビュー アーキテクチャでは、いくつかの状況に適していません。 これらの例を検討してください。

- Windows を C で記述されたアプリケーションを移植する場合は、アプリケーションにドキュメント/ビューのサポートを追加する前に、ポートを完了する可能性があります。

- 簡単なユーティリティを作成する場合、ドキュメント/ビュー アーキテクチャせずに行えることがあります。

- 場合は、元のコードは既にデータ管理とデータをどのように表示、移動、コード、ドキュメント/ビュー モデルには労力を費やす価値、2 つを分離する必要がありますので。 コードのままにしたい場合があります。

ドキュメント/ビュー アーキテクチャを使用しないアプリケーションを作成するには、オフ、**ドキュメント/ビュー アーキテクチャ サポート**MFC アプリケーション ウィザードの手順 1 でのチェック ボックス。 参照してください[MFC アプリケーション ウィザード](../mfc/reference/mfc-application-wizard.md)詳細についてはします。

> [!NOTE]
>  MFC アプリケーション ウィザードによって生成されたダイアログ ベースのアプリケーションは、ドキュメント/ビュー アーキテクチャを使用しないため、**ドキュメント/ビュー アーキテクチャ サポート**ダイアログ アプリケーションの種類を選択した場合に、チェック ボックスが無効になっています。

ソースとダイアログ エディターと同様に、Visual C ウィザードで生成されたアプリケーションと同様に動作ウィザードで生成されたその他のアプリケーションと同じです。 アプリケーションは、ツールバー、スクロール バー、およびステータス バーの場合は、サポートし、は、**について**ボックス。 アプリケーションは、ドキュメント テンプレートを登録できませんし、ドキュメントのクラスは含まれません。

生成されたアプリケーションのビュー クラスでは、注`CChildView`から派生した`CWnd`します。 MFC では、作成し、アプリケーションによって作成されたフレーム ウィンドウ内でビュー クラスの 1 つのインスタンスを配置します。 MFC で依然ビュー ウィンドウを使用して配置して、アプリケーションのコンテンツの管理が簡素化されます。 描画コードを追加することができます、`OnPaint`このクラスのメンバー。 コードは、フレームではなく、ビューにスクロール バーを追加する必要があります。

ない場合は、プロジェクト内では MFC によって提供されるドキュメント/ビュー アーキテクチャは、アプリケーションの基本的な機能の多くを実装する責任を負いますであるために、アプリケーションの多くの重要な機能の実装を担当していることを意味します。

- MFC アプリケーション ウィザードによって提供されるため、アプリケーションのメニューのみを含む**新規**と**終了**コマンドを**ファイル**メニュー。 (、**新規**MDI アプリケーションでのみコマンドがサポートされている、ドキュメント/ビューなしいない SDI アプリケーションをサポートします)。生成されたメニュー リソースは、MRU (最近使用された) リストをサポートしていません。

- ハンドラー関数を含む、アプリケーションをサポートする任意のコマンドの実装を追加する必要があります**オープン**と**保存**上、**ファイル**メニュー。 MFC は、サポートは、ドキュメント/ビュー アーキテクチャに密接にバインドされたが、通常、これらの機能をサポートするためにコードを提供します。

- ツールバー、アプリケーションは、1 つは、要求した場合、最小限に場合なります。

ウィザードは、適切な MFC アーキテクチャを保証するため、ドキュメント/ビュー アーキテクチャを備えていないアプリケーションを作成する MFC アプリケーション ウィザードを使用することを強くお勧めします。 ただし、ウィザードの使用を避ける必要がある場合、は、コード内のドキュメント/ビュー アーキテクチャをバイパスするようにいくつかの方法。

- 未使用の拡張子として、ドキュメントを処理し、ビュー クラスで、上記のように、データ管理コードを実装します。 ドキュメントのオーバーヘッドが比較的少ないです。 1 つ[CDocument](../mfc/reference/cdocument-class.md)オブジェクトは、少量のオーバーヘッドを単独での少量のオーバーヘッドを発生`CDocument`の基本クラス、 [CCmdTarget](../mfc/reference/ccmdtarget-class.md)と[CObject](../mfc/reference/cobject-class.md)します。 後者のクラスの両方が小さいです。

   宣言されている`CDocument`:

  - 2 つ`CString`オブジェクト。

  - 次の 3 つ**BOOL**秒。

  - 1 つ`CDocTemplate`ポインター。

  - 1 つ`CPtrList`ドキュメントのビューの一覧を含むオブジェクトです。

  さらに、ドキュメントには、ドキュメント オブジェクト、そのオブジェクトの表示、フレーム ウィンドウ、およびドキュメントのテンプレート オブジェクトを作成する時間が必要です。

- ドキュメントとビューの両方を使いませんとして扱います。 ビューではなく、フレーム ウィンドウで、データ管理と描画コードを配置します。 この方法は、C 言語のプログラミング モデルに近いです。

- MFC フレームワークのドキュメントとまったく作成されないようにビューを作成する部分を上書きします。 呼び出しで、ドキュメントの作成プロセスが始まる`CWinApp::AddDocTemplate`します。 アプリケーション クラスには、その呼び出しを排除`InitInstance`メンバー関数を内のフレーム ウィンドウを作成する代わりに、`InitInstance`自分でします。 フレーム ウィンドウ クラスには、データ管理コードを配置します。 ドキュメント/ビューの作成プロセスを示した[ドキュメント/ビューの作成](../mfc/document-view-creation.md)です。 これはより多くの作業であり、フレームワークのより深い理解が必要ですが、すべてのドキュメント/ビューのオーバーヘッドがなくなり。

この記事[MFC:データベース クラスのないドキュメントとビューを使用して](../data/mfc-using-database-classes-without-documents-and-views.md)データベース アプリケーションのコンテキストでのドキュメント/ビューの代替手段より具体的な例を示しています。

## <a name="see-also"></a>関連項目

[ドキュメント/ビュー アーキテクチャ](../mfc/document-view-architecture.md)
