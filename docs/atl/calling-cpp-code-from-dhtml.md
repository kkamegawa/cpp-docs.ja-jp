---
title: DHTML から C++ コードを呼び出す
ms.date: 11/04/2016
helpviewer_keywords:
- DHTML, calling C++ code from
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
ms.openlocfilehash: fb63f8671770f57972a4c789d983bdf9658d5ecb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62251735"
---
# <a name="calling-c-code-from-dhtml"></a>DHTML から C++ コードを呼び出す

DHTML コントロールは、テスト コンテナーまたは Internet Explorer などのコンテナーでホストできます。 参照してください[テスト プロパティとテスト コンテナーでイベント](../mfc/testing-properties-and-events-with-test-container.md)テスト コンテナーにアクセスする方法についてはします。

コントロールをホストするコンテナーは、通常の制御のインターフェイスを使用して、コントロールと通信します。 DHTML、C++ コードと HTML のリソースと通信するには、"UI"で終わるディスパッチ インターフェイスを使用します。 [ATL DHTML コントロールの変更](../atl/modifying-the-atl-dhtml-control.md)、これらの異なるインターフェイスによって呼び出されるメソッドの追加方法を練習することができます。

DHTML から C++ コードの呼び出しの例を参照する[DHTML コントロール作成](../atl/creating-an-atl-dhtml-control.md)ATL コントロール ウィザードを使用して、HTML ファイルとヘッダー ファイル内のコードを確認します。

## <a name="declaring-webbrowser-methods-in-the-header-file"></a>ヘッダー ファイル内の WebBrowser メソッドを宣言します。

DHTML UI から C++ のメソッドを呼び出すには、コントロールの UI のインターフェイスにメソッドを追加する必要があります。 たとえば、ATL コントロール ウィザードによって作成されたヘッダー ファイルには、C++ メソッドが含まれます。 `OnClick`、ウィザードで生成されたコントロールの UI インターフェイスのメンバーであります。

調べる`OnClick`コントロールの .h ファイルには。

[!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/cpp/calling-cpp-code-from-dhtml_1.h)]

最初のパラメーターでは、 *pdispBody*、本体オブジェクトのディスパッチ インターフェイスへのポインターです。 2 番目のパラメーターでは、 *varColor*コントロールに適用する色を識別します。

## <a name="calling-c-code-in-the-html-file"></a>HTML ファイルでの C++ コードを呼び出す

ヘッダー ファイル内の WebBrowser メソッドを宣言した後は、HTML ファイルからメソッドを呼び出すことができます。 ATL コントロール ウィザードが次の 3 つの Windows ディスパッチ メソッドに挿入される HTML ファイルでの通知: 次の 3 つ`OnClick`コントロールの背景色を変更するメッセージをディスパッチするメソッド。

HTML ファイル内のメソッドのいずれかを確認します。

`<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`

ウィンドウの外部メソッドでは、上の HTML コードで`OnClick`、button タグの一部としてと呼びます。 メソッドには 2 つのパラメーター: `theBody`、HTML ドキュメントの本文を参照して`"red"`ボタンがクリックされたときに、コントロールの背景色が赤に変更されることを示します。 `Red`ボタンのラベルは、次のタグ。

参照してください[ATL DHTML コントロールの変更](../atl/modifying-the-atl-dhtml-control.md)詳細については、独自のメソッドを提供します。 参照してください[DHTML コントロール プロジェクトの要素の識別](../atl/identifying-the-elements-of-the-dhtml-control-project.md)HTML ファイルの詳細についてはします。

## <a name="see-also"></a>関連項目

[DHTML コントロールのサポート](../atl/atl-support-for-dhtml-controls.md)
