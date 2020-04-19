---
title: MFC ActiveX コントロール:シリアル化します。
ms.date: 09/12/2018
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
helpviewer_keywords:
- MFC ActiveX controls [MFC], version support
- wVerMinor global constant [MFC]
- GetVersion method [MFC]
- ExchangeVersion method [MFC]
- MFC ActiveX controls [MFC], serializing
- DoPropExchange method [MFC]
- versioning ActiveX controls
- wVerMajor global constant
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
ms.openlocfilehash: 0c1c845640be2dfaa6aeda2defb478afb650b83b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324741"
---
# <a name="mfc-activex-controls-serializing"></a>MFC ActiveX コントロール:シリアル化します。

この記事では、ActiveX コントロールをシリアル化する方法について説明します。 シリアル化は、ディスク ファイルなどの永続的なストレージ メディアに対するから読み取りまたは書き込みのプロセスです。 Microsoft Foundation Class (MFC) ライブラリでは、クラスでシリアル化の組み込みサポート`CObject`します。 `COleControl` プロパティの交換機構を使用して ActiveX コントロールには、このサポートを拡張します。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

ActiveX コントロールのシリアル化をオーバーライドすることで実装[使って](../mfc/reference/colecontrol-class.md#dopropexchange)します。 、この関数は、読み込み中に呼び出され、メンバー変数またはメンバー変数の変更通知を使用して実装するすべてのプロパティを格納する、コントロール オブジェクトの保存します。

次のトピックでは、ActiveX コントロールのシリアル化に関連する主な問題を説明します。

- 実装する`DoPropExchange`コントロール オブジェクトをシリアル化関数

- [シリアル化プロセスをカスタマイズします。](#_core_customizing_the_default_behavior_of_dopropexchange)

- [バージョンのサポートを実装します。](#_core_implementing_version_support)

##  <a name="_core_implementing_the_dopropexchange_function"></a> DoPropExchange 関数を実装します。

コントロール プロジェクトを生成する ActiveX コントロール ウィザードを使用するといくつかの既定のハンドラー関数がの既定の実装を含む、コントロール クラスに自動的に追加[使って](../mfc/reference/colecontrol-class.md#dopropexchange)します。 次の例では、ActiveX コントロール ウィザードで作成されたクラスに追加するコードを示します。

[!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

プロパティで持続されるようにする場合は、変更`DoPropExchange`プロパティ exchange 関数への呼び出しを追加します。 次の例では、CircleShape プロパティが、既定の値を持つ、カスタム ブール CircleShape プロパティのシリアル化**TRUE**:

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

次の表では、コントロールのプロパティをシリアル化に使用できる有効なプロパティ exchange 関数を示します。

|プロパティの exchange 関数|目的|
|---------------------------------|-------------|
|**PX_Blob( )**|型のバイナリ ラージ オブジェクト (BLOB) データのプロパティをシリアル化します。|
|**PX_Bool( )**|ブール型のプロパティをシリアル化します。|
|**PX_Color( )**|カラーの型のプロパティをシリアル化します。|
|**PX_Currency( )**|型をシリアル化**CY** (通貨) プロパティ。|
|**PX_Double( )**|型をシリアル化**double**プロパティ。|
|**PX_Font( )**|フォントの type プロパティをシリアル化します。|
|**PX_Float( )**|型をシリアル化**float**プロパティ。|
|**PX_IUnknown( )**|型のプロパティをシリアル化`LPUNKNOWN`します。|
|**PX_Long( )**|型をシリアル化**long**プロパティ。|
|**PX_Picture( )**|Picture プロパティの型をシリアル化します。|
|**PX_Short( )**|型をシリアル化**short**プロパティ。|
|**PXstring( )**|型をシリアル化`CString`プロパティ。|
|**PX_ULong( )**|型をシリアル化**ULONG**プロパティ。|
|**PX_UShort( )**|型をシリアル化**USHORT**プロパティ。|

これらのプロパティ exchange 関数の詳細については、次を参照してください。[永続化の OLE コントロール](../mfc/reference/persistence-of-ole-controls.md)で、 *MFC リファレンス*します。

##  <a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> DoPropExchange の既定の動作をカスタマイズします。

既定の実装`DoPropertyExchange`基底クラスへの呼び出しは、(前のトピックを参照) として`COleControl`します。 これで自動的にサポートされるプロパティのセットをシリアル化`COleControl`コントロールのカスタム プロパティのみをシリアル化するよりも多くのストレージ領域が使用されます。 重要な検討するプロパティのみをシリアル化するオブジェクトをこの呼び出しを削除できます。 保存または明示的に追加しない限り、コントロール オブジェクトを読み込むとき、コントロールが実装されているストック プロパティの状態はシリアルされない**px _** に呼び出します。

##  <a name="_core_implementing_version_support"></a> バージョンのサポートを実装します。

バージョン サポートでは、新しい永続的なプロパティを追加しを検出し、コントロールの以前のバージョンで作成された永続的な状態の読み込みができる変更後の ActiveX コントロールができます。 コントロールのバージョンを使用できるようにする、持続データの一部として、呼び出す[COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion) 、コントロールの`DoPropExchange`関数。 ActiveX コントロールは、ActiveX コントロール ウィザードを使用して作成された場合、この呼び出しが自動的に挿入されます。 バージョンのサポートが必要でない場合に削除することができます。 ただし、コントロールのサイズでコストは非常に小さい (4 バイト) のバージョンのサポートを提供する柔軟性を高めします。

コントロールが ActiveX コントロール ウィザードで作成されていない場合は、呼び出しを追加`COleControl::ExchangeVersion`の先頭に次の行を挿入することで、`DoPropExchange`関数 (呼び出しの前に`COleControl::DoPropExchange`)。

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

いずれかを使用することができます**DWORD**としてバージョン番号。 ActiveX コントロール ウィザードによって生成されたプロジェクトを使用して、`_wVerMinor`と`_wVerMajor`既定値として。 これらは、プロジェクトの ActiveX コントロール クラスの実装ファイルで定義されるグローバル定数です。 内の残りの部分で、`DoPropExchange`関数を呼び出すことができます[CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion)いつでも保存または取得するバージョンを取得します。

このサンプルのコントロールのバージョン 1 では次の例では、"ReleaseDate"プロパティのみがあります。 バージョン 2 では、"OriginalDate"プロパティを追加します。 コントロールの指示に従って、以前のバージョンからの永続的な状態の読み込みには、これと既定値に新しいプロパティのメンバー変数を初期化します。

[!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

既定では、コントロールを「変換」古いデータを最新の形式にします。 たとえば、バージョン 2 のコントロールがバージョン 1 で保存されたデータを読み込む場合をもう一度保存すると、バージョン 2 の形式を書き込むことが。 コントロールで形式最後に読み取られたデータを保存する場合は、渡す**FALSE**を呼び出すときに、3 番目のパラメーターとして`ExchangeVersion`します。 この 3 番目のパラメーターは省略可能で、 **TRUE**既定。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)
