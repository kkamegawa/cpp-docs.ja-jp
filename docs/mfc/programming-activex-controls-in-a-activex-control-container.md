---
title: ActiveX コントロール コンテナー:ActiveX コントロール コンテナーで ActiveX コントロールのプログラミング
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- Confirm Classes dialog box
- wrapper classes [MFC], ActiveX controls
- ActiveX control containers [MFC], wrapper classes
- ActiveX controls [MFC], accessing
- MFC ActiveX controls [MFC], accessing in containers
- header files [MFC], for ActiveX control wrapper class
- wrapper classes [MFC], using
- ActiveX controls [MFC], wrapper classes
ms.assetid: ef9b2480-92d6-4191-b16e-8055c4fd7b73
ms.openlocfilehash: eaeb5275ce825272e1c605e7ceeefa24db7a32ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378116"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>ActiveX コントロール コンテナー:ActiveX コントロール コンテナーで ActiveX コントロールのプログラミング

この記事は、公開されているにアクセスするためのプロセスを説明します[メソッド](../mfc/mfc-activex-controls-methods.md)と[プロパティ](../mfc/mfc-activex-controls-properties.md)の埋め込みの ActiveX コントロール。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

基本的には、次の手順には。

1. [ActiveX コンテナー プロジェクトに ActiveX コントロールを挿入](../mfc/inserting-a-control-into-a-control-container-application.md)ギャラリーを使用します。

1. [メンバー変数を定義する](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)(またはその他の形式のアクセス)、ActiveX と同じ型のラッパー クラスを制御します。

1. [ActiveX コントロールをプログラム](#_core_programming_the_activex_control)ラッパー クラスのメンバー関数を使用して事前に定義します。

詳細については、この ActiveX コントロール サポート (名前付きコンテナー) ダイアログ ベースのプロジェクトを作成したを想定しています。 円のサンプル コントロール円, は、結果のプロジェクトに追加されます。

プロジェクト (ステップ 1) に、円のコントロールを挿入すると後、は、円のコントロールのインスタンスをアプリケーションのメイン ダイアログ ボックスに挿入します。

## <a name="procedures"></a>手順

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>円コントロール ダイアログ テンプレートを追加するには

1. ActiveX コントロール コンテナーのプロジェクトを読み込みます。 この例では、使用、`Container`プロジェクト。

1. リソース ビュー タブをクリックします。

1. 開く、**ダイアログ**フォルダー。

1. メイン ダイアログ ボックスのテンプレートをダブルクリックします。 この例では、使用**で**します。

1. ツールボックスに円コントロール アイコンをクリックします。

1. 円のコントロールを挿入 ダイアログ ボックス内のスポットをクリックします。

1. **ファイル** メニューの 選択**すべて保存** ダイアログ ボックスのテンプレートのすべての変更を保存します。

## <a name="modifications-to-the-project"></a>プロジェクトの変更

円のコントロールにアクセスするコンテナー アプリケーションを有効にする Visual C に自動的に追加しますラッパー クラス (`CCirc`) 実装ファイル (します。CPP) コンテナー プロジェクトをラッパー クラスのヘッダー (します。H)、ダイアログ ボックスのヘッダー ファイルへのファイル:

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

##  <a name="_core_the_wrapper_class_header_28h29_file"></a> ラッパー クラスのヘッダー (します。H) ファイル

プロパティを取得および設定 (しメソッドを呼び出す)、円のコントロールの`CCirc`ラッパー クラスが公開されているすべてのメソッドとプロパティの宣言を提供します。 例では、これらの宣言内にある可変範囲H. 次の例は、クラスの部分`CCirc`ActiveX コントロールの公開されているインターフェイスを定義します。

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

これらの関数は、通常の C++ 構文を使用して、アプリケーションのプロシージャの他の呼び出すことができます。 このメンバー関数は、コントロールのメソッドとプロパティにアクセスできる設定の使用に関する詳細については、セクションをご覧ください。 [ActiveX コントロールをプログラミング](#_core_programming_the_activex_control)します。

##  <a name="_core_member_variable_modifications_to_the_project"></a> プロジェクトにメンバー変数の変更

ActiveX コントロールは、プロジェクトに追加され、ダイアログ ボックスのコンテナーに埋め込まれているとは、プロジェクトの他の部分でアクセスできます。 コントロールにアクセスする最も簡単な方法が、[メンバー変数を作成](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)ダイアログ クラスの`CContainerDlg`(ステップ 2)、つまり Visual C によってプロジェクトに追加するラッパー クラスと同じ型。 埋め込まれたコントロールをいつでもアクセスし、メンバー変数を使用できます。

ときに、**メンバー変数の追加** ダイアログ ボックスを追加、*で*メンバー変数をプロジェクトにも追加します、次の行をヘッダー ファイル (します。H) の`CContainerDlg`クラス。

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

さらに、呼び出しを**DDX_Control**が自動的に追加、`CContainerDlg`の実装の`DoDataExchange`:

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

##  <a name="_core_programming_the_activex_control"></a> ActiveX コントロールのプログラミング

この時点では、ダイアログ テンプレートに ActiveX コントロールを挿入して、メンバー変数を作成します。 埋め込まれたコントロールのメソッドとプロパティへのアクセスに共通の C++ 構文を使用できます。

説明したように (で[ラッパー クラスのヘッダー (します。H) ファイル](#_core_the_wrapper_class_header_28h29_file))、ヘッダー ファイル (します。H) の`CCirc`このケースの可変範囲内のラッパー クラスH には、取得し、公開されているプロパティ値を設定に使用できるメンバー関数の一覧が含まれています。 公開されたメソッドのメンバー関数も使用できます。

コントロールのプロパティを変更する一般的な場所は、`OnInitDialog`メイン ダイアログ クラスのメンバー関数。 ダイアログ ボックスが表示され、そのコントロールのいずれかを含む、その内容を初期化するために使用する前にのみ、この関数が呼び出されます。

次のコード例では、*で*メンバー変数に埋め込まれた円のコントロールのキャプションと CircleShape プロパティを変更します。

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>関連項目

[ActiveX コントロール コンテナー](../mfc/activex-control-containers.md)
