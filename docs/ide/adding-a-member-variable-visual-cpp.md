---
title: メンバー変数を追加する
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.variable
- vc.codewiz.variable.overview
helpviewer_keywords:
- member variables, adding
- member variables
- add member variable wizard [C++]
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
ms.openlocfilehash: 0f10b4867b443f0db69743d7ff23bb059290b0a5
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328962"
---
# <a name="add-a-member-variable"></a>メンバー変数を追加する

クラス ビューを使用して、クラスにメンバー変数を追加することができます。 メンバー変数は、[データ交換とデータの入力規則](../mfc/dialog-data-exchange-and-validation.md)に使用するか、一般にすることができます。 データ メンバー変数ウィザードは、関連情報を取得し、それを使用して適切な場所のソース ファイル内に要素を挿入するために設計されています。 [リソース ビュー](../windows/how-to-create-a-resource-script-file.md#create-resources)の[ダイアログ エディター](../windows/dialog-editor.md)から、または[クラス ビュー](/visualstudio/ide/viewing-the-structure-of-code)からメンバー変数を追加できます。

> [!NOTE]
> ダイアログ ボックスを設計および実装しているときに、ダイアログ エディターを使用して、ダイアログ ボックス コントロールを追加し、コントロールのメンバー変数を実装するとより効率的である場合があります。

**メンバー変数の追加ウィザードを使用して、リソース ビューにダイアログ コントロールのメンバー変数を追加するには:**

1. リソース ビューでプロジェクト ノードとダイアログ ノードを展開して、プロジェクトのダイアログ ボックスのリストを表示します。

1. メンバー変数を追加するダイアログ ボックスをダブルクリックして、ダイアログ エディターで開きます。

1. ダイアログ エディターに表示されたダイアログ ボックスで、メンバー変数を追加するコントロールを右クリックします。

1. ショートカット メニューで、**[変数の追加]** を選択して[メンバー変数の追加ウィザード](#add-member-variable-wizard)を表示します。

   > [!NOTE]
   > 既定値が既に**コントロール ID** に提供されています。

1. 適切なウィザード ボックスに情報を指定します。 詳細については、「[ダイアログ ボックス コントロールおよび変数の型](#dialog-box-controls-and-variable-types)」を参照してください。

1. **[完了]** を選択して、プロジェクトに定義と実装コードを追加し、ウィザードを閉じます。

**メンバー変数の追加ウィザードを使用して、クラス ビューからメンバー変数を追加するには:**

1. [クラス ビュー](/visualstudio/ide/viewing-the-structure-of-code)でプロジェクト ノードを展開して、プロジェクト内のクラスを表示します。

1. 変数を追加するクラスを右クリックします。

1. ショートカット メニューで、**[追加]**、**[変数の追加]** の順に選択して、メンバー変数の追加ウィザードを表示します。

1. 適切なウィザード ボックスに情報を指定します。 詳細については、「[メンバー変数の追加ウィザード](#add-member-variable-wizard)」を参照してください。

1. **[完了]** を選択して、プロジェクトに定義と実装コードを追加し、ウィザードを閉じます。

## <a name="in-this-section"></a>このセクションの内容

- [メンバー変数の追加ウィザード](#add-member-variable-wizard)
- [ダイアログ ボックス コントロールおよび変数の型](#dialog-box-controls-and-variable-types)

## <a name="add-member-variable-wizard"></a>メンバー変数の追加ウィザード

このウィザードでは、ヘッダー ファイルにメンバー変数宣言を追加できます。 オプションによっては、.cpp ファイルにコードを追加できます。 このウィザードを使用してメンバー変数を追加すると、開発環境でそのコードを編集できます。

- **アクセス**

  メンバー変数へのアクセス権を設定します。 アクセス修飾子とは、メンバー変数に対して他のクラスが持つアクセス権を指定するキーワードです。 アクセス権の指定の詳細については、「[メンバー アクセス コントロール](../cpp/member-access-control-cpp.md)」を参照してください。 メンバー変数のアクセス レベルは、既定では `public` に設定されます。

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

- **変数の型**

  追加するメンバー変数の戻り値の型を設定します。

  - ダイアログ ボックス コントロールではないメンバー変数を追加する場合は、利用可能な型のリストから選択します。

    戻り値の型については、「[基本型](../cpp/fundamental-types-cpp.md)」を参照してください。

    |||
    |-|-|
    |`char`|`short`|
    |`double`|`unsigned char`|
    |`float`|`unsigned int`|
    |`int`|`unsigned long`|
    |`long`||

  - ダイアログ ボックス コントロールのメンバー変数を追加する場合、このボックスにはコントロールまたは値に対して返されるオブジェクトの型が入力されます。 **[コントロール]** を選択した場合、**[変数の型]** により **[コントロール ID]** ボックスで選択したコントロールの基底クラスが指定されます。 ダイアログ ボックス コントロールに値を保持することができ、**[値]** を選択した場合、**[変数の型]** によってコントロールで保持できる値の適切な型が指定されます。 詳細については、「[ダイアログ ボックス コントロールおよび変数の型](#dialog-box-controls-and-variable-types)」を参照してください。

    この値は、**[コントロール ID]** の選択内容によって異なり、変更することができません。

- **変数名**

  追加するメンバー変数の名前を設定します。 メンバー変数は、通常、既定で提供されている識別用文字列 `m_` で始まります。

- **Control variable (コントロール変数)**

  メンバー変数が、[データ交換とデータの検証](../mfc/dialog-data-exchange-and-validation.md)をサポートしているダイアログ ボックス内のコントロールを管理することを示します。 詳細については、[DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) に関するセクションを参照してください。 このオプションは、[CDialog](../mfc/reference/cdialog-class.md) から派生したクラスに追加されたメンバー変数に対してのみ使用可能です。 **[コントロール ID]** と **[コントロール型]** オプションをアクティブ化するには、このボックスを選択します。

- **コントロール ID**

  追加するコントロール変数の ID を設定します。 メンバー変数を追加するコントロールの型の ID をリストから選択します。 このリストは、**[コントロール変数]** ボックスが選択されている場合にのみアクティブとなり、さらにダイアログ ボックスに既に追加されているコントロールの ID に限定されます。 たとえば、標準的な **[OK]** ボタンの場合、コントロール ID は **IDOK** です。

  |オプション|説明|
  |------------|-----------------|
  |**コントロール**|このオプションは、既定でコントロール型に設定されます。 このオプションでは、コントロールの状態やコンテンツ (リスト ボックス、コンボ ボックス、または編集ボックスで管理するように) ではなく、コントロール自体が管理されます。|
  |**[値]**|このオプションは、編集ボックスやチェック ボックスなど、値を保持したり状態を表示したりできるコントロール型で使用できます。 これはまた、範囲、コンテンツ、または状態の管理対象となるコントロール型でも利用できます。 詳細については、「[ダイアログ ボックス コントロールおよび変数の型](#dialog-box-controls-and-variable-types)」を参照してください。|

- **カテゴリ**

  変数の基となるのが、コントロールの種類とコントロール値のどちらであるかを指定します。

- **コントロール型**

  追加するコントロールの型を設定します。 このボックスは、変更できません。 たとえば、ボタンは **BUTTON** というコントロール型を持ち、コンボ ボックスは **COMBOBOX** というコントロール型を持ちます。 詳細については、「[ダイアログ ボックス コントロールおよび変数の型](#dialog-box-controls-and-variable-types)」を参照してください。

- **最大文字数**

  **[変数の型]** が [[CString]](../atl-mfc-shared/reference/cstringt-class.md) に設定されている場合にのみ使用できます。 コントロールで保持できる文字数の最大限度を示します。

- **最小値**

  変数の型が `BOOL`、`int`、`UINT`、`long`、`DWORD`、`float`、`double`、`BYTE`、`short`、[COLECurrency](../mfc/reference/colecurrency-class.md)、または [CTime](../atl-mfc-shared/reference/ctime-class.md) である場合にのみ使用できます。 スケールまたは日付の範囲に許容される最小値を示します。

- **最大値**

  変数の型が `BOOL`、`int`、`UINT`、`long`、`DWORD`、`float`、`double`、`BYTE`、`short`、`COLECurrency`、または `CTime` である場合にのみ使用できます。 スケールまたは日付の範囲に許容される最大値を示します。

- **.h ファイル**

  ActiveX コントロール場合、そのメンバー変数にはラッパー クラスが必要です。 ヘッダー ファイルの名前を設定し、クラス宣言を追加します。

- **.cpp ファイル**

  ActiveX コントロール場合、そのメンバー変数にはラッパー クラスが必要です。 実装ファイルの名前を設定し、クラス定義を追加します。

- **コメント**

  メンバー変数のヘッダー ファイルにコメントを挿入します。

## <a name="dialog-box-controls-and-variable-types"></a>ダイアログ ボックス コントロールおよび変数の型

[メンバー変数の追加ウィザード](#add-member-variable-wizard)を使用すると、MFC で作成したダイアログ ボックス コントロールにメンバー変数を追加できます。 メンバー変数を追加するコントロールの種類によって、ダイアログ ボックスに表示されるオプションが決まります。

次の表は、MFC と[ダイアログ エディター](../windows/dialog-editor.md)でサポートされているすべてのダイアログ ボックス コントロール型をまとめたものです。 また、それらの使用可能な型と値も示されています。

|コントロール|コントロール型|コントロール変数の型|値変数の型|最小/最大値 (値の型のみ)|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|アニメーション コントロール|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|なし、コントロールのみ|N/A|
|ボタン|ボタン|[CButton](../mfc/reference/cbutton-class.md)|なし、コントロールのみ|N/A|
|チェック ボックス|チェック|[CButton](../mfc/reference/cbutton-class.md)|`BOOL`|最小値/最大値|
|コンボ ボックス|コンボ ボックス|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|最大文字数|
|日時指定コントロール|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|最小値/最大値|
|エディット ボックス|編集|[CEdit](../mfc/reference/cedit-class.md)|`CString`、int、UINT、long、DWORD、float、double、BYTE、short、BOOL、`COleDateTime`、または `COleCurrency`|最小値/最大値、一部は最大文字数をサポート|
|ホット キー コントロール|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|なし、コントロールのみ|N/A|
|リスト ボックス|リスト ボックス|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|最大文字数|
|リスト コントロール|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|なし、コントロールのみ|N/A|
|月間予定表コントロール|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|最小値/最大値|
|プログレス コントロール|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|なし、コントロールのみ|N/A|
|リッチ エディット 2 コントロール|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|最大文字数|
|リッチ エディット コントロール|RICHEDIT|`CRichEditCtrl`|`CString`|最大文字数|
|スクロール バー (垂直または水平)|SCROLLBAR|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|最小値/最大値|
|Slider コントロール|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|最小値/最大値|
|スピン コントロール|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|なし、コントロールのみ|N/A|
|タブ コントロール|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|なし、コントロールのみ|N/A|
|ツリー コントロール|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|なし、コントロールのみ|N/A|
