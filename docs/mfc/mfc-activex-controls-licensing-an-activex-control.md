---
title: MFC ActiveX コントロール:ActiveX コントロールのライセンス
ms.date: 11/19/2018
f1_keywords:
- COleObjectFactory
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
ms.openlocfilehash: eda2ea08c6bd3526befb71c704aa20eba6935b04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392759"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC ActiveX コントロール:ActiveX コントロールのライセンス

ライセンス サポート、ActiveX コントロールのオプション機能できますが、使用、またはコントロールを配布できるユーザーを制御します。 (ライセンスの問題の詳細については、ライセンスの問題を参照してください[既存の ActiveX コントロールのアップグレード](../mfc/upgrading-an-existing-activex-control.md)。)。

> [!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

この記事では、次のトピックについて説明します。

- [ActiveX コントロールのライセンスの概要](#_core_overview_of_activex_control_licensing)

- [ライセンス付きコントロールを作成します。](#_core_creating_a_licensed_control)

- [ライセンスのサポート](#_core_licensing_support)

- [ActiveX コントロールのライセンスをカスタマイズします。](#_core_customizing_the_licensing_of_an_activex_control)

ライセンスを実装する ActiveX コントロールでは、他のユーザーが ActiveX コントロールを使用する方法を決定する、コントロールの開発者として使用する、できます。 コントロールにコントロールの購入者を指定するとします。使用許諾契約書ファイルを契約しない場合は、コントロールを配布できます購入者にことにします。コントロールを使用するアプリケーションでの使用許諾契約書ファイルです。 これは、最初からコントロールをライセンスすることがなく、コントロールを使用する新しいアプリケーションの記述からそのアプリケーションのようにします。

##  <a name="_core_overview_of_activex_control_licensing"></a> ActiveX コントロールのライセンスの概要

ActiveX コントロールのライセンスのサポートを提供する、 [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)クラスにいくつかの関数の実装を提供する、`IClassFactory2`インターフェイス: `IClassFactory2::RequestLicKey`、`IClassFactory2::GetLicInfo`と`IClassFactory2::CreateInstanceLic`します。 コンテナー アプリケーションの開発者がコントロールへの呼び出しのインスタンスを作成する要求を作成するときに`GetLicInfo`されることを確認するコントロール。使用許諾契約書ファイルが存在します。 コントロールのライセンスが与えられた場合、コントロールのインスタンスは作成され、コンテナー内に配置されます。 開発者は、コンテナー アプリケーションの構築が終了したら、別の関数を呼び出すには、この時間`RequestLicKey`になります。 この関数は、コンテナー アプリケーションにライセンス キー (単純な文字列) を返します。 返されたキーは、アプリケーションで埋め込まれます。

次の図では、コンテナー アプリケーションの開発時に使用される ActiveX コントロールのライセンス認証を示します。 前述のように、コンテナー アプリケーションの開発者には、適切な必要があります。コントロールのインスタンスを作成する開発用コンピューターにインストールされている使用許諾契約書ファイルです。

![ActiveX コントロールの開発時で検証をライセンス](../mfc/media/vc374d1.gif "ライセンスされた ActiveX コントロールの開発時で検証") <br/>
開発時の ActiveX コントロールのライセンス検査

次の図に示すように、次のプロセスでは、エンド ユーザー コンテナー アプリケーションを実行するときに発生します。

アプリケーションが開始されると、作成する、通常は、コントロールのインスタンス必要があります。 コンテナーでは、これを実現するを呼び出すことによって`CreateInstanceLic`、埋め込まれているライセンス キーのパラメーターとして渡します。 文字列比較が埋め込まれているライセンス キーとライセンス キーのコントロールのコピーになります。 一致が成功した場合は、コントロールのインスタンスを作成し、アプリケーションは正常に実行を継続します。 なお、します。使用許諾契約書ファイルでは、コントロールのユーザーのコンピューター上に存在する必要はありません。

![実行時に検証する ActiveX コントロールのライセンス](../mfc/media/vc374d2.gif "ライセンスされた ActiveX コントロールの実行時に検証") <br/>
実行時の ActiveX コントロールのライセンス検査

コントロールのライセンスの 2 つの基本的なコンポーネントで構成されています: DLL のコントロール実装で特定のコードとライセンス ファイル。 コードは、2 つ (または 3 つ) の関数呼び出しと、「ライセンス文字列」、著作権情報を格納するいると呼ぶ文字列で構成されます。 これらの呼び出しとライセンスの文字列がコントロールの実装が見つかりました (します。CPP) ファイルです。 ActiveX コントロール ウィザード、によって生成された、ライセンス ファイルは、著作権表記を含むテキスト ファイルです。 という名前でプロジェクト名を使用して、します。例ではサンプルの使用許諾契約書拡張子。使用許諾契約書します。 ライセンス付きコントロールは、デザイン時の使用が必要な場合、ライセンス ファイルを添付してください。

##  <a name="_core_creating_a_licensed_control"></a> ライセンス付きコントロールを作成します。

ActiveX コントロール ウィザードを使用して制御フレームワークを作成する場合は、ライセンス サポートに簡単です。 コントロールは実行時のライセンスである必要がありますを指定すると、ActiveX コントロール ウィザードは、ライセンスをサポートするために、コントロール クラスにコードを追加します。 ライセンス認証のキーおよびライセンス ファイルを使用する関数のコードで構成されます。 これらの関数は、コントロールのライセンスをカスタマイズすることも変更できます。 ライセンスのカスタマイズの詳細については、次を参照してください。[ライセンス ActiveX コントロールのカスタマイズ](#_core_customizing_the_licensing_of_an_activex_control)この記事で後述します。

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>コントロール プロジェクトを作成するときに、ActiveX コントロール ウィザードを使用してライセンスのサポートを追加するには

1. 」の指示に従って[MFC ActiveX コントロールの作成](../mfc/reference/creating-an-mfc-activex-control.md)です。 **アプリケーション設定**ActiveX コントロール ウィザードのページには、実行時のライセンスを持つコントロールを作成するオプションが含まれています。

今すぐ、ActiveX コントロール ウィザードには、基本ライセンスのサポートが含まれる ActiveX コントロールのフレームワークが生成されます。 ライセンス コードの詳細については、次のトピックを参照してください。

##  <a name="_core_licensing_support"></a> ライセンスのサポート

ActiveX コントロール ウィザードを使用して ActiveX コントロールへのライセンスのサポートを追加すると、ファイルを宣言し、ライセンスの機能を実装するコードは、コントロールのヘッダーと実装を追加、ActiveX コントロール ウィザードが追加されます。 このコードは、`VerifyUserLicense`メンバー関数と`GetLicenseKey`メンバー関数にある既定の実装をオーバーライド[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)します。 これらの関数は、取得し、コントロールのライセンスを確認します。

> [!NOTE]
>  3 番目のメンバー関数`VerifyLicenseKey`ActiveX コントロール ウィザードでは生成されませんが、ライセンス キーの検証動作をカスタマイズする上書きできます。

これらのメンバー関数は次のとおりです。

- [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   コントロールで、システムは、コントロールのライセンス ファイルの存在をチェックして、デザイン時の使用状況を確認します。 この関数`IClassFactory2::GetLicInfo`と`IClassFactory::CreateInstanceLic`します。

- [GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   コントロールの DLL からの一意のキーを要求します。 このキーがコンテナー アプリケーションに埋め込まれ、後と組み合わせて使用`VerifyLicenseKey`コントロールのインスタンスを作成します。 この関数`IClassFactory2::RequestLicKey`します。

- [VerifyLicenseKey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   埋め込みのキーと、コントロールの一意のキーは、同じであることを確認します。 これにより、使用するためのコントロールのインスタンスを作成するコンテナーです。 この関数`IClassFactory2::CreateInstanceLic`ライセンス キーのカスタマイズされた検証を提供するオーバーライドできます。 既定の実装では、文字列比較を実行します。 詳細については、次を参照してください。[ライセンス ActiveX コントロールのカスタマイズ](#_core_customizing_the_licensing_of_an_activex_control)、この記事で後述します。

###  <a name="_core_header_file_modifications"></a> ヘッダー ファイルの変更

ActiveX コントロール ウィザードでは、コントロールのヘッダー ファイルに次のコードを配置します。 この例の 2 つのメンバー関数で`CSampleCtrl`オブジェクト 's`factory`宣言され、いずれかのコントロールの存在を確認します。使用許諾契約書ファイルと別のコントロールを含むアプリケーションで使用されるライセンス キーを取得する:

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

###  <a name="_core_implementation_file_modifications"></a> 実装ファイルの変更

ActiveX コントロール ウィザードでは、次の 2 つのステートメントをファイル名のライセンスとライセンスの文字列を宣言する、コントロール実装ファイルに配置します。

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
>  変更する場合`szLicString`何らかの方法では、コントロールの最初の行も変更する必要があります。使用許諾契約書ファイルまたはライセンスは正しく機能しません。

ActiveX コントロール ウィザード、コントロール クラスの定義、コントロール実装ファイルに次のコードを配置する`VerifyUserLicense`と`GetLicenseKey`関数。

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

最後に、 **ActiveX コントロール ウィザード**コントロール プロジェクトを変更します。IDL ファイルです。 **ライセンス**キーワードは、次の例のように、コントロールのコクラスの宣言に追加されます。

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> ActiveX コントロールのライセンスをカスタマイズします。

`VerifyUserLicense`、 `GetLicenseKey`、および`VerifyLicenseKey`コントロールのライセンスの動作をカスタマイズできるコントロールのファクトリ クラスの仮想メンバー関数として宣言されます。

たとえば、複数のレベルのオーバーライドすることで、コントロールのライセンスを行うことができます、`VerifyUserLicense`または`VerifyLicenseKey`メンバー関数。 この関数の内部では、し、検出されたライセンス レベルに従ってユーザーに公開するプロパティやメソッドを調整できます。

コードを追加することも、`VerifyLicenseKey`作成を制御するユーザーに通知が失敗したためにカスタマイズしたメソッドを提供する関数。 たとえば、`VerifyLicenseKey`コントロールが初期化に失敗したことを示すメッセージを表示することがメンバー関数のボックスとその理由です。

> [!NOTE]
>  ActiveX コントロールのライセンス認証をカスタマイズする別の方法は、呼び出す代わりに、特定のレジストリ キーの登録情報データベースを確認することです。`AfxVerifyLicFile`します。 既定の実装の例は、次を参照してください。、[実装ファイルの変更](#_core_implementation_file_modifications)この記事の「します。

ライセンスの問題の詳細については、ライセンスの問題を参照してください。[既存の ActiveX コントロールのアップグレード](../mfc/upgrading-an-existing-activex-control.md)します。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX コントロール ウィザード](../mfc/reference/mfc-activex-control-wizard.md)
