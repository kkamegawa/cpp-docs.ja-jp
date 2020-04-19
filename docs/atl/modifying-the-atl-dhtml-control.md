---
title: ATL DHTML コントロールの変更
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, modifying
- DHTML controls
- DHTML controls, modifying
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
ms.openlocfilehash: e594360cc6752a60bf2e07a1fb1d02041604d959
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503005"
---
# <a name="modifying-the-atl-dhtml-control"></a>ATL DHTML コントロールの変更

ATL コントロール ウィザードは、ビルドして、コントロールを実行し、プロジェクト ファイルで、メソッドを記述する方法と DHTML からディスパッチ メソッドを使用して、コントロールの C++ コードを呼び出す方法を確認できるように、スタート コードを提供します。 インターフェイスにディスパッチ メソッドを追加することができます。 次に、HTML リソースでメソッドを呼び出すことができます。

## <a name="to-modify-the-atl-dhtml-control"></a>ATL DHTML コントロールを変更するには

1. **クラス ビュー**、コントロール プロジェクトを展開します。

   1 つのメソッドは"UI"で終わるインターフェイス`OnClick`します。 "UI"で終わらないインターフェイスには、すべてのメソッドはありません。

1. というメソッドを追加`MethodInvoked`"UI"で終わらないインターフェイス

   このメソッドは、DHTML コントロールとやり取りするために使用するインターフェイスが、コンテナーの対話のコントロールのコンテナーで使用されるインターフェイスに追加されます。 コンテナーのみでは、このメソッドを呼び出すことができます。

1. .Cpp ファイルにスタブ メソッドを検索し、たとえば、メッセージ ボックスを表示するコードを追加します。

   [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_1.cpp)]

1. という別のメソッドを追加`HelloHTML`、この時点で、のみ"UI"で終わるインターフェイスに追加します。 スタブとして作成された出力を検索`HelloHTML`.cpp でメソッド ファイルし、たとえば、メッセージ ボックスを表示するコードを追加します。

   [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_2.cpp)]

1. 3 番目のメソッドを追加`GoToURL`、"UI"で終わらないインターフェイス このメソッドを呼び出すことによって実装[IWebBrowser2::Navigate](/previous-versions//aa752133\(v=vs.85\))、次のようにします。

   [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_3.cpp)]

   使用することができます、`IWebBrowser2`メソッド ATL の .h ファイルでそのインターフェイスへのポインターを提供するためです。

次に、作成したメソッドを呼び出す HTML リソースを変更します。 これらのメソッドを呼び出すための 3 つのボタンを追加します。

## <a name="to-modify-the-html-resource"></a>HTML リソースを変更するには

1. **ソリューション エクスプ ローラー**、HTML リソースを表示する .htm ファイルをダブルクリックします。

   HTML、特に、外部の Windows ディスパッチ メソッドの呼び出しを確認します。 HTML の呼び出し、プロジェクトの`OnClick`メソッドとパラメーターは、コントロールの本体を示します (`theBody`) と色を割り当てる ("`red`")。 メソッドの呼び出しに続くテキストは、ボタンに表示されるラベルです。

1. もう 1 つ追加`OnClick`メソッド、色の変更のみです。 例:

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>
    ```

   このメソッドでは、ラベルのボタンを作成します。**更新**、ユーザーがコントロールを、元の白い背景に返されるクリックできます。

1. 呼び出しを追加、`HelloHTML`メソッドを作成します。 例:

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>
    ```

   このメソッドでは、ラベルのボタンを作成します。 **HelloHTML**、表示するユーザーがクリックできる、`HelloHTML`メッセージ ボックス。

今すぐビルドすることができますと[変更 DHTML コントロールのテスト](../atl/testing-the-modified-atl-dhtml-control.md)します。

## <a name="see-also"></a>関連項目

[DHTML コントロールのサポート](../atl/atl-support-for-dhtml-controls.md)
