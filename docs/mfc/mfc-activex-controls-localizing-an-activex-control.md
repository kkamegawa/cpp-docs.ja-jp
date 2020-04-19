---
title: MFC ActiveX コントロール:ActiveX コントロールのローカライズ
ms.date: 09/12/2018
f1_keywords:
- LocaleID
- AfxOleRegisterTypeLib
helpviewer_keywords:
- localization, ActiveX controls
- MFC ActiveX controls [MFC], localizing
- LocaleID ambient property [MFC]
- LOCALIZE sample [MFC]
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
ms.openlocfilehash: 13c8ff545763017b01685e012ab2d497eaf7084a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392688"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>MFC ActiveX コントロール:ActiveX コントロールのローカライズ

この記事では、ActiveX コントロールのインターフェイスをローカライズするための手順について説明します。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

国際市場に ActiveX コントロールを調整する場合は、コントロールをローカライズしたい場合があります。 Windows では、既定の英語、ドイツ語、フランス語、スウェーデン語を含むだけでなく多くの言語をサポートします。 これは、場合、そのインターフェイスは、英語でのみはコントロールの問題が生じる。

一般に、ActiveX コントロール常に基に、ロケール LocaleID アンビエント プロパティ。 これには、次の 3 つの方法があります。

- LocaleID アンビエント プロパティの現在の値に基づいて、オンデマンドで常に、リソースを読み込みます。 MFC ActiveX コントロールをサンプル[LOCALIZE](../overview/visual-cpp-samples.md)この戦略を使用します。

- LocaleID アンビエント プロパティに基づいて、最初のコントロールがインスタンス化時にリソースを読み込むし、他のすべてのインスタンスにこれらのリソースを使用します。 この記事では、この方法について説明します。

    > [!NOTE]
    >  これは機能しません正しく場合によっては、将来のインスタンスが別のロケールがある場合。

- 使用して、`OnAmbientChanged`通知関数をコンテナーのロケールの適切なリソースを動的に読み込みます。

    > [!NOTE]
    >  これは、コントロールの機能しますが、ランタイム DLL に動的に更新されません、独自のリソース LocaleID アンビエント プロパティが変更されたとき。 さらに、ActiveX コントロール用の Dll は実行時では、スレッドのロケールを使用して、そのリソースのロケールを決定します。

この記事の残りの部分では、2 つのローカライズ方法について説明します。 第 1 の戦略[コントロールのプログラミング インターフェイスをローカライズ](#_core_localizing_your_control.92.s_programmability_interface)(プロパティ、メソッド、およびイベントの名前)。 2 番目の方法[コントロールのユーザー インターフェイスをローカライズ](#_core_localizing_the_control.92.s_user_interface)コンテナーの LocaleID アンビエント プロパティを使用します。 コントロールのローカリゼーションのデモについては、MFC ActiveX コントロールのサンプルを参照してください。 [LOCALIZE](../overview/visual-cpp-samples.md)します。

##  <a name="_core_localizing_your_control.92.s_programmability_interface"></a> コントロールのプログラミング インターフェイスのローカライズ

コントロールのプログラミング インターフェイス (コントロールを使用するアプリケーションを記述するプログラマによって使用されるインターフェイス) をローカライズする場合は、変更済みのコントロールを作成する必要があります。IDL は、(コントロールのタイプ ライブラリを構築するためのスクリプト) をサポートする各言語のファイルします。 これは、コントロールのプロパティ名をローカライズする必要がある唯一の場所です。

ローカライズされたコントロールを開発する際に、タイプ ライブラリ レベルで属性としてロケール ID が含まれます。 たとえば、フランス語のローカライズされたプロパティ名を持つタイプ ライブラリを提供する場合は、サンプルのコピーを作成します。IDL ファイルを開き、SAMPLEFR を付けます。IDL です。 (フランス語のロケール ID は 0x040c です)、ファイルにロケール ID 属性を追加、次のようにします。

[!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]

SAMPLEFR のプロパティ名を変更します。フランス語としを使用して MKTYPLIB に IDL です。EXE、フランス語を生成するためには、ライブラリ、SAMPLEFR を入力します。TLB します。

複数のローカライズされたタイプ ライブラリを作成するには、ローカライズされたいずれかを追加します。IDL ファイルをプロジェクトと、自動的に構築されます。

#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>追加します。ActiveX コントロール プロジェクトへの IDL ファイル

1. コントロール プロジェクトを開いて、**プロジェクト** メニューのをクリックして**既存項目の追加**します。

   **既存項目の追加** ダイアログ ボックスが表示されます。

1. 必要に応じて、ドライブとを表示するディレクトリを選択します。

1. **ファイルの種類**ボックスで、**すべてのファイル (\*.\*)**.

1. ファイルの一覧ボックスをダブルクリックします。IDL ファイルがプロジェクトに挿入します。

1. をクリックして**オープン**すべての必要なときに追加します。IDL ファイル。

ファイルがプロジェクトに追加されて、残りのプロジェクトのビルド時にビルドされます。 ローカライズされたタイプ ライブラリは、ActiveX コントロールの現在のプロジェクト ディレクトリに配置されます。

コード内の (通常は、英語) で内部プロパティ名は常に使用し、はローカライズされません。 これには、コントロールのディスパッチ マップ、プロパティの exchange 関数、およびプロパティ ページ データ交換コードが含まれます。

1 つだけのタイプ ライブラリ (します。コントロールの実装のリソースに TLB) ファイルを連結することも (します。OCX) ファイルです。 これは、標準化されたバージョンでは、通常は (通常は、英語) の名前。 出荷する必要があるコントロールのローカライズされたバージョンを出荷します。OCX (これは、既定値に既にバインドされています。TLB バージョン) とします。適切なロケールの TLB します。 これだけであることを意味します。正しい以降は、英語バージョンでは、OCX が必要です。TLB に既にバインドされています。 その他のロケールのローカライズされたタイプ ライブラリも配布するには、します。OCX します。

コントロールのクライアントが、ローカライズされたタイプ ライブラリを見つけることを確認するには、ロケール固有を登録します。Windows システム レジストリのタイプ ライブラリ セクション TLB ファイル。 3 番目のパラメーター (通常は省略可能)、 [AfxOleRegisterTypeLib](../mfc/reference/registering-ole-controls.md#afxoleregistertypelib)関数がこの目的に使用されます。 次の例では、ActiveX コントロールのフランス語のタイプ ライブラリを登録します。

[!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]

コントロールが登録されているときに、`AfxOleRegisterTypeLib`関数は、指定したを自動的に検索します。コントロールと同じディレクトリに TLB ファイル、Windows の登録データベースに登録します。 場合、します。TLB ファイルが見つからない場合は、関数が影響を与えません。

##  <a name="_core_localizing_the_control.92.s_user_interface"></a> コントロールのユーザー インターフェイスのローカライズ

コントロールのユーザー インターフェイスをローカライズするには、言語固有のリソース Dll にすべてのプロパティ ページとエラー メッセージ) などのコントロールのユーザーに表示されるリソースを配置します。 コンテナーの LocaleID アンビエント プロパティを使用して、ユーザーのロケールの適切な DLL を選択することができます。

次のコード例では、検索して特定のロケールのリソース DLL を読み込む方法の 1 つを示します。 このメンバー関数と呼ばれる`GetLocalizedResourceHandle`この例では、ActiveX コントロール クラスのメンバー関数を指定できます。

[!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]

専門的なローカライズを提供する、switch ステートメントの各ケースで、サブ言語 ID を確認することに注意してください。 この関数の例については、次を参照してください。、`GetResourceHandle`関数では、MFC ActiveX コントロール サンプル[LOCALIZE](../overview/visual-cpp-samples.md)します。

呼び出すことができます、コントロール最初の読み込み時にそれ自体をコンテナーに、 [COleControl::AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid)ロケール ID を取得するには コントロールは、返されたロケール ID の値を渡すことができますし、`GetLocalizedResourceHandle`関数で、適切なリソースのライブラリを読み込みます。 コントロールが存在する場合、結果のハンドルを渡す必要がありますに[AfxSetResourceHandle](../mfc/reference/application-information-and-management.md#afxsetresourcehandle):

[!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]

上記のコード サンプルに、メンバー関数のオーバーライドなど、コントロールの配置[COleControl::OnSetClientSite](../mfc/reference/colecontrol-class.md#onsetclientsite)します。 さらに、 *m_hResDLL*コントロール クラスのメンバー変数にする必要があります。

コントロールのプロパティ ページをローカライズするための同様のロジックを使用できます。 プロパティ ページをローカライズするには、プロパティ ページの実装ファイルに次の例のようなコードを追加 (のオーバーライドで[COlePropertyPage::OnSetPageSite](../mfc/reference/colepropertypage-class.md#onsetpagesite))。

[!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)
