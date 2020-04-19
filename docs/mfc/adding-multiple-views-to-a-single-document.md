---
title: シングル ドキュメントへのマルチ ビューの追加
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 593c59c73b58b4364c9d652ce8eb415c17af496c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394742"
---
# <a name="adding-multiple-views-to-a-single-document"></a>シングル ドキュメントへのマルチ ビューの追加

Microsoft Foundation Class (MFC) ライブラリで作成されたシングル ドキュメント インターフェイス (SDI) アプリケーションで各ドキュメントの種類は、1 つのビューの種類に関連付けられます。 場合によってに新しいビューを使用して、ドキュメントの現在のビューを切り替えることができることをお勧めします。

> [!TIP]
>  1 つのドキュメントに複数のビューを実装する追加手順については、次を参照してください。 [CDocument::AddView](../mfc/reference/cdocument-class.md#addview)と[収集](../overview/visual-cpp-samples.md)MFC サンプル。

この機能を実装するには、新しい追加`CView`の派生クラスと既存の MFC アプリケーションを動的に、ビューを切り替えるためのコードを追加します。

手順は次のとおりです。

- [既存のアプリケーションのクラスを変更します。](#vcconmodifyexistingapplicationa1)

- [作成し、新しいビュー クラスを変更します。](#vcconnewviewclassa2)

- [作成し、新しいビューのアタッチ](#vcconattachnewviewa3)

- [切り替え関数を実装します。](#vcconswitchingfunctiona4)

- [ビューの切り替えのサポートを追加します。](#vcconswitchingtheviewa5)

このトピックの残りの部分には、次の前提としています。

- 名前、`CWinApp`の派生オブジェクトが`CMyWinApp`、および`CMyWinApp`が宣言されで定義されている*MYWINAPP します。H*と*MYWINAPP します。CPP*します。

- `CNewView` 新しい名前を指定`CView`の派生オブジェクト、および`CNewView`が宣言されで定義されている*NEWVIEW します。H*と*NEWVIEW します。CPP*します。

##  <a name="vcconmodifyexistingapplicationa1"></a> 既存のアプリケーションのクラスを変更します。

ビューに切り替えるには、アプリケーションのビューとそれらを切り替えるメソッドを格納するメンバー変数を追加して、アプリケーション クラスを変更する必要があります。

宣言に次のコードを追加`CMyWinApp`で*MYWINAPP します。H*:

[!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

新しいメンバー変数、`m_pOldView`と`m_pNewView`、現在のビューと新しく作成されたものを指すようにします。 新しいメソッド (`SwitchView`) がユーザーによって要求されたときにビューを切り替えます。 メソッドの本体はこのトピックの後半で説明[切り替え関数の実装](#vcconswitchingfunctiona4)します。

最後の変更、アプリケーション クラスには、Windows メッセージを定義する新しいヘッダー ファイルを含める必要があります (**WM_INITIALUPDATE**) 切り替え関数で使用されています。

Include セクションでは、次の行を挿入*MYWINAPP します。CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

変更を保存し、次の手順に進みます。

##  <a name="vcconnewviewclassa2"></a> 作成し、新しいビュー クラスを変更します。

新しいビュー クラスは、簡単に作成を使用して、**クラスの新しい**クラス ビューで使用できるコマンド。 このクラスの唯一の要件がから派生して`CView`します。 この新しいクラスをアプリケーションに追加します。 新しいクラスをプロジェクトに追加する方法については、次を参照してください。[クラスの追加](../ide/adding-a-class-visual-cpp.md)します。

クラスをプロジェクトに追加した後は、一部のビュー クラス メンバーのアクセシビリティを変更する必要があります。

変更*NEWVIEW します。H*からアクセス指定子を変更することで**保護**に**パブリック**コンス トラクターとデストラクターの。 これで、クラスの作成し、破棄を動的にして、表示する前に、ビューの外観を変更します。

変更を保存し、次の手順に進みます。

##  <a name="vcconattachnewviewa3"></a> 作成し、新しいビューのアタッチ

作成、新しいビューをアタッチするには変更する必要があります、`InitInstance`アプリケーション クラスの関数。 新しい表示オブジェクトし初期化両方を作成する新しいコードを追加、変更`m_pOldView`と`m_pNewView`2 つの既存のビュー オブジェクト。

内で新しいビューが作成されるため、`InitInstance`関数、新規および既存の両方のビューは、アプリケーションの有効期間にわたって永続化します。 ただし、アプリケーションでは、新しいビューが動的に作成簡単でした。

呼び出し後にこのコードを挿入`ProcessShellCommand`:

[!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

変更を保存し、次の手順に進みます。

##  <a name="vcconswitchingfunctiona4"></a> 切り替え関数を実装します。

前の手順で作成され、新しいビュー オブジェクトを初期化するコードを追加します。 最後の主要な部分は、切り替えのメソッドを実装する`SwitchView`します。

アプリケーション クラスの実装ファイルの末尾 (*MYWINAPP します。CPP*)、次のメソッド定義を追加します。

[!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

変更を保存し、次の手順に進みます。

##  <a name="vcconswitchingtheviewa5"></a> ビューの切り替えのサポートを追加します。

最後の手順では、呼び出すコードを追加、`SwitchView`メソッド、アプリケーションは、ビューに切り替える必要がある場合。 これは、いくつかの方法で行うことができます。 によって、ユーザーを選択するための新しいメニュー項目を追加するか、特定の条件が満たされたときに、内部的には、ビューを切り替えます。

新しいメニュー項目とコマンド ハンドラー関数を追加する方法の詳細については、次を参照してください。[コマンドとコントロール通知のハンドラー](../mfc/handlers-for-commands-and-control-notifications.md)します。

## <a name="see-also"></a>関連項目

[ドキュメント/ビュー アーキテクチャ](../mfc/document-view-architecture.md)
