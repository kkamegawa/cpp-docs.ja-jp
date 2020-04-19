---
title: MFC クラス追加ウィザード
ms.date: 09/06/2019
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
ms.openlocfilehash: 2c82e084de2123c579299ca6490bdfcfdac5d255
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908029"
---
# <a name="mfc-add-class-wizard"></a>MFC クラス追加ウィザード

このコードウィザードを使用して、既存の MFC プロジェクトにクラスを追加するか、MFC をサポートする ATL プロジェクトにクラスを追加します。 Mfc をサポートする Win32 プロジェクトに MFC クラスを追加することもできます。 プロジェクトの作成時に指定した機能によって、このダイアログボックスで使用できるオプションが決まります。 ウィザードにアクセスするには、[クラスの**クラスの追加**[ウィザード](mfc-class-wizard.md)] をクリックします。

![MFC クラス追加ウィザード](media/add-mfc-class-wizard.png "MFC クラス追加ウィザード")

## <a name="names"></a>名前

このページでは、新しいクラスのクラス名、基本クラス、およびファイル名を指定します。

- **クラス名**

  新しいクラスの名前を指定し、このページの Id とファイルの名前の既定の基準を提供します。 C++通常、クラスは "C" で始まります。たとえば、"CMyClass" は "MyClass" になります。

- **基本クラス**

  新しいクラスの基本クラスの名前を指定します。 既定では、基本クラスは[CWnd](../../mfc/reference/cwnd-class.md)です。 選択した基本クラスによって、このページの他のボックスがアクティブかどうかが決まります。

  基底クラスとして設定したクラスの型によって、クラスにダイアログ ID またはリソース ID があるかどうかが決まります。 一般的なクラスの種類は次のとおりです。

  - ダイアログ ID またはリソース ID を必要としない、 [CButton](../../mfc/reference/cbutton-class.md)、 [CWnd](../../mfc/reference/cwnd-class.md)、または[CDocument](../../mfc/reference/cdocument-class.md)などのクラス。 これらのクラスは、ダイアログまたはリソース ID を使用しません。 基底クラスに対してこれらのクラスのいずれかを選択すると、 **[ダイアログ ID]** ボックスと **[DHTML リソース ID]** ボックスが淡色表示になります。

  - ダイアログ ID を必要とする、 [CDialog](../../mfc/reference/cdialog-class.md)、 [CFormView](../../mfc/reference/cformview-class.md)、 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)などのクラス。

  - クラス[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)。ダイアログ ID、DHTML リソース ID、および HTML ファイル名が必要です。

  ダイアログ ID を必要とするクラスでは、[リソースエディター](../../windows/resource-editors.md)を使用してダイアログリソースを作成し、[クラスウィザード](mfc-class-wizard.md)でその ID を割り当てて、そのリソース id に関連付けられたクラスを作成する方が効率的な場合があります。 標準の Windows ダイアログボックスの作成の詳細については[、「新しいダイアログボックスの作成](../../windows/creating-a-new-dialog-box.md)」を参照してください。

  > [!NOTE]
  > ダイアログリソースを最初に作成し、から`CDHtmlDialog`その新しいクラスを派生させる場合は、既定のダイアログボックスに表示される標準の [Windows **OK]** ボタンと **[キャンセル**] ボタンを削除します。 標準の [Windows] ダイアログボックスは、独自の **[OK]** ボタンと **[キャンセル**] ボタンを含む DHTML フォームをホストします。

  ダイアログボックスには、Windows コントロールと DHTML コントロールの両方を含めることができますが、推奨されません。

- **ダイアログ ID**

  **基本クラス**として、、、また`CDHtmlDialog`は`CDialog`を`CFormView`選択`CPropertyPage`した場合のダイアログの ID を指定します。

- **.h ファイル**

  新しいオブジェクトのクラスにヘッダー ファイルの名前を設定します。 既定では、この名前は、 **[クラス名]** で指定した名前に基づきます。 選択した場所にファイル名を保存するには、あるいはクラス宣言を既存のファイルに追加するには、省略記号ボタンをクリックします。 既存のファイルを選択した場合、ウィザードで **[完了]** をクリックするまで、ファイルは選択した場所に保存されません。

  ウィザードではファイルは上書きされません。 既存のファイルの名前を選択する場合、 **[完了]** をクリックすると、ウィザードからクラス宣言をファイルのコンテンツに追加するかどうかを指定するように求められます。 ファイルを追加するには、 **[はい]** をクリックします。ウィザードに戻り、別のファイル名を指定するには、 **[いいえ]** をクリックします。

- **.cpp ファイル**

  新しいオブジェクトのクラスに実装ファイルの名前を設定します。 既定では、この名前は、 **[クラス名]** で指定した名前に基づきます。 ファイル名を選択した場所に保存するには、省略記号ボタンをクリックします。 ファイルは、ウィザードで **[完了]** をクリックするまで選択した場所に保存されません。

  ウィザードではファイルは上書きされません。 既存のファイルの名前を選択する場合、 **[完了]** をクリックすると、ウィザードからクラスの実装をファイルのコンテンツに追加するかどうかを指定するように求められます。 ファイルを追加するには、 **[はい]** をクリックします。ウィザードに戻り、別のファイル名を指定するには、 **[いいえ]** をクリックします。

- **アクティブなアクセシビリティ**

  コンストラクターで[Enableactiveaccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility)を呼び出すことによって、MFC が Active Accessibility をサポートできるようにします。 このオプションは、 [CWnd](../../mfc/reference/cwnd-class.md)から派生したクラスで使用できます。

- **オートメーション**

  [オートメーション](../../mfc/automation.md)のクラスレベルのサポートを設定します。 クラスレベルでのオートメーションは、オートメーションをサポートするすべてのクラスで使用できます。 また、オートメーションをサポートするように作成されたプロジェクトでも使用できます。 つまり、 [ATL をサポート](../../atl/reference/mfc-support-in-atl-projects.md)する mfc プロジェクトか、Mfc アプリケーションウィザードの[[高度な機能](../../mfc/reference/advanced-features-mfc-application-wizard.md)] ページで **[オートメーション]** チェックボックスをオンにした mfc プロジェクトのいずれかです。

   次の基底クラスでは、オートメーションサポートを利用できません。

  - `CAsyncMonitorFile`

  - `CAsyncSocket`

  - `CCachedDataPathProperty`

  - `CConnectionPoint`

  - `CDatabase`

  - `CDataPathProperty`

  - `CHttpFilter`

  - `CHttpServer`

  - `CInternetSession`

  - `CObject`

  - `CSocket`

## <a name="see-also"></a>関連項目

[MFC クラス](../../mfc/reference/adding-an-mfc-class.md)<br/>
[クラスの追加](../../ide/adding-a-class-visual-cpp.md)
