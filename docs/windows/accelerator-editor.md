---
title: アクセラレータ エディター (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator.F1
- vc.editors.accelerator
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [C++], accelerator key
- accelerator keys [C++]
- resource editors [C++], Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
- searching, in accelarator tables
- accelerator tables [C++], finding entries
- accelerator tables [C++], adding entries
- New Accelerator command
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
- accelerator tables [C++], copying entries
- rc files [C++], moving an accelerator table entry
- .rc files [C++], moving accelerator table entries
- accelerator tables [C++], moving entries
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
ms.openlocfilehash: f5ae9880719a3a8b799ea8deb751b6f0a85542bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391037"
---
# <a name="accelerator-editor-c"></a>アクセラレータ エディター (C++)

アクセラレータ テーブルは、ショートカット キー、およびそれらに関連付けられたコマンド識別子と呼ばれる、アクセラレータ キーの一覧を含む C++ Windows リソースです。 プログラムは複数のアクセラレータ テーブルを持つことができます。

通常、アクセラレータはメニューやツール バーでも使用できるプログラム コマンドのキーボード ショートカットとして使用されます。 しかし、アクセラレータ テーブルを使用すると、関連付けられているユーザー インターフェイス オブジェクトのないコマンドにキーの組み合わせを定義できます。

> [!TIP]
> 使用する場合、**アクセラレータ エディター**、右クリックすると、頻繁にコマンドのショートカット メニューを表示します。 使用できるコマンドは、ポインターの位置によって異なります。

[クラス ビュー](/visualstudio/ide/viewing-the-structure-of-code) を使用して、コードにアクセス キーのコマンドをフックできます。 定義済みのアクセラレータ キーの一覧は、次を参照してください。[アクセラレータ キー](../windows/predefined-accelerator-keys.md)します。

> [!NOTE]
> Windows には、空のアクセラレータ テーブルを作成することを指定できません。 エントリがないアクセラレータ テーブルを作成すると、テーブルを保存する際に自動的に削除されます。

## <a name="accelerator-properties"></a>アクセラレータのプロパティ

アクセラレータのプロパティで設定できる、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)いつでもです。 使用することも、**アクセラレータ エディター**アクセラレータ テーブルでアクセラレータのプロパティを変更します。 使用して行われた変更、**プロパティ**ウィンドウまたは**アクセラレータ エディター**結果は同じ、アクセラレータ テーブルでの編集をすぐに反映されます。

**ID**プロパティは、プログラム コード内の各アクセラレータ テーブル エントリを参照します。 このエントリは、プログラムを受け取る、アクセラレータ キーまたはキーの組み合わせを押すとコマンドの値です。 メニュー項目と同じアクセラレータとする、 **ID**同じとして非常に長い、 **ID**アクセラレータのテーブルと同じです、 **ID**メニュー リソース。

各アクセラレータ**ID**は 3 つのプロパティがあります。**修飾子**、**キー**、および**型**

**修飾子**プロパティは、アクセラレータ キーの組み合わせをコントロールに設定します。

> [!NOTE]
> **プロパティ**ウィンドウで、**修飾子**プロパティは、3 つの異なるとして表示されます。**ブール**プロパティ、すべてのことができますが個別に制御。**Alt キーを押し**、 **Ctrl**、および**Shift**します。

有効なエントリを次に、**修飾子**アクセラレータ テーブル内のプロパティ。

   |[値]|説明|
   |-----------|-----------------|
   |**None**|ユーザーが押したのみ、**キー**値。<br/><br/>として解釈される ASCII]/[ANSI 値 001 026、経由でこの値は使用が最も効果的に ^ A ~ ^ Z (**Ctrl + A**を通じて**Ctrl + Z**)。|
   |**Alt**|ユーザーが押す必要があります**Alt**する前に、**キー**値。|
   |**Ctrl**|ユーザーが押す必要があります**Ctrl**する前に、**キー**値、ASCII 型が無効です。|
   |**Shift**|ユーザーが押す必要があります**Shift**する前に、**キー**値。|
   |**Ctrl + Alt**|ユーザーが押す必要があります**Ctrl**と**Alt**する前に、**キー**値、ASCII 型が無効です。|
   |**Ctrl + Shift**|ユーザーが押す必要があります**Ctrl**と**Shift**する前に、**キー**値、ASCII 型が無効です。|
   |**Alt + Shift**|ユーザーが押す必要があります**Alt**と**Shift**する前に、**キー**値、ASCII 型が無効です。|
   |**Ctrl + Alt + Shift**|ユーザーが押す必要があります**Ctrl**、 **Alt**と**Shift**する前に、**キー**値、ASCII 型が無効です。|

**キー**プロパティは、アクセス キーとして使用する実際のキーを設定します。

有効なエントリを次に、**キー**アクセラレータ テーブル内のプロパティ。

   |[値]|説明|
   |-----------|-----------------|
   |0 ~ 255 の 10 進形式の範囲の整数。|値は、値が ASCII または ANSI として次のように扱われるかどうかを決定します。<br/><br/>   -1 桁の数字は、常に、ASCII または ANSI の値ではなく、対応するキーとして解釈されます。<br/>   の 1 ~ 26、ゼロが付く場合から値として解釈されます ^ A ~ ^ Z で押されたときに、アルファベットの文字の ASCII 値を表す、 **Ctrl**キーが押し続けられます。<br/>   の 27 ~ 32 値は常に、3 桁の 10 進値 027 ~ 032 として解釈されます。<br/>   -前に 0 がまたはいない、ANSI 値として解釈されるかどうかに 033 ~ 255 の値です。|
   |1 つのキーボード文字。|A ~ Z の大文字または数字 0 - 9 は、ASCII または仮想キー値のいずれかを指定できます。 その他の任意の文字には ASCII のみです。|
   |A ~ Z の範囲内の 1 つのキーボード文字 (大文字のみ) など、キャレット (^) に続く ^ C.|と一緒に押したときに、このオプションは、キーの ASCII 値を入力、 **Ctrl**キーが押し続けられます。|
   |有効な仮想キー識別子。|ドロップ ダウン**キー**アクセラレータ テーブル内のボックスには、標準の仮想キー識別子の一覧が含まれています。|

> [!NOTE]
> ASCII 値を入力するときに、**修飾子**プロパティのオプションは制限されています。 使用するため利用可能な唯一のコントロール キーは、 **Alt**キー。

> [!TIP]
> アクセラレータ キーを定義するショートカットがエントリを右クリックするか、アクセラレータ テーブルの複数のエントリには、選択し、 **キー タイピング登録**キーボードのキーまたはキーの組み合わせのいずれかのキーを押します。
>
> これは、 **キー タイピング登録**コマンドが表示されます、**編集**メニュー。

**型**プロパティは、ショートカット キーの組み合わせが、アクセス キーに関連付けられているかどうかを決定します。 **ID** ASCII/ANSI キーの値または仮想キー (VIRTKEY) の組み合わせとして解釈されます。

- 場合、**型**プロパティは**ASCII**、**修飾子**プロパティがありますのみ`None`または`Alt`アクセラレータ、を使用することができますか**Ctrl**キー、前のキーで指定したとおり、`^`します。

- 場合、**型**プロパティは**VIRTKEY**、任意に組み合わせた**修飾子**と**キー**値が無効です。

> [!NOTE]
> アクセラレータ テーブルに値を入力と ASCII/ANSI、select として扱われます値がする場合、**型**クリックし、テーブル内のエントリを**ASCII**ドロップダウン リストから。 ただし、使用する場合、 **キー タイピング登録**コマンドを**編集**を指定するメニュー、**キー**、変更する必要があります、**型**からプロパティ**VIRTKEY**に**ASCII** *する前に*入力、**キー**コード。

## <a name="accelerator-tables"></a>アクセラレータ テーブル

インプレース編集を直接アクセラレータ テーブルを編集する C++ プロジェクトで、**アクセラレータ エディター**します。

以下の手順は、標準のプロパティ ページの使用を参照してください、ただし、インプレース編集とプロパティ ページのメソッドの両方にある同じ結果になります。 プロパティ ページを使用して、またはインプレース編集を使用して行われた変更は、アクセラレータ テーブルですぐに反映されます。

### <a name="to-edit-in-an-accelerator-table"></a>アクセラレータ テーブルで編集するには

1. アイコンをダブルクリックして、アクセラレータ テーブルを開く[リソース ビュー](how-to-create-a-resource-script-file.md#create-resources)します。

1. テーブルでエントリを選択し、インプレース編集をアクティブ化を選択します。

1. ドロップダウン コンボ ボックスから選択するか、または変更する入力します。

   - **ID**でリストまたは入力して編集を選択します。

   - **修飾子**を一覧から選択します。

   - **キー**でリストまたは入力して編集を選択します。

   - **型**、 **ASCII**または**VIRTKEY**一覧から。

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>開いているアクセラレータ テーブルでエントリを検索するには

1. アイコンをダブルクリックして、アクセラレータ テーブルを開く[リソース ビュー](how-to-create-a-resource-script-file.md#create-resources)します。

1. 列の内容をアルファベット順に並べ替える列見出しを選択します。 たとえば、 **ID**アクセラレータ テーブル内のすべての Id をアルファベット順に表示します。

   これで、一覧に目を通しながらエントリを探すことができます。

### <a name="to-add-an-entry-to-an-accelerator-table"></a>アクセラレータ テーブルにエントリを追加するには

1. アイコンをダブルクリックして、アクセラレータ テーブルを開く[リソース ビュー](how-to-create-a-resource-script-file.md#create-resources)します。

1. アクセラレータ テーブル内で右クリックし、**新しいアクセラレータ**、またはテーブルの下部にある空の行エントリを選択します。

1. 選択、 **ID**でドロップダウン リストから、 **ID**ボックスか、新しい入力*ID*で、 **ID**ボックス。

1. 型、*キー* 、アクセラレータとして使用するか右クリックして選択する**キー タイピング登録**キーの組み合わせを設定またはメニューに移動する**編集** >  **キー タイピング登録**します。

1. 変更、**修飾子**と**型**、必要に応じてキーを押します**Enter**します。

> [!NOTE]
> 定義するすべてのアクセラレータが一意であることを確認します。 たとえば、同じ ID に割り当てられているいくつかのキーの組み合わせがあることができます**Ctrl**+**P**と**F8**どちらも ID_PRINT に割り当てる割り当てすることができます。 ただし、1 つ以上の ID はたとえば、機能しませんに割り当てられているキーの組み合わせを持つ**Ctrl**+**Z** ID_SPELL_CHECK と ID_THESAURUS の両方に割り当てられます。

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>アクセラレータ テーブルのエントリを削除するには

1. アイコンをダブルクリックして、アクセラレータ テーブルを開く[リソース ビュー](how-to-create-a-resource-script-file.md#create-resources)します。

1. 削除、または押したするエントリを選択、 **Ctrl**または**Shift**複数のエントリを選択することを選択するのにはキー。

1. 右クリックし、**削除**、メニューに移動または**編集** > **削除**します。

> [!TIP]
> 押すことも、**削除**を削除するキー。

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>アクセラレータ テーブルのエントリを別のリソース スクリプト ファイルに移動またはコピーするには

1. 両方のリソース スクリプト ファイルでアクセラレータ テーブルを開き、移動するエントリを選択します。

1. **編集**] メニューの [選択**コピー**または**切り取り**します。

1. ターゲット リソース スクリプト ファイルとの間にエントリを選択、**編集**] メニューの [選択**貼り付け**します。

> [!NOTE]
> コピーと貼り付けのショートカット キーも使用できます。

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>複数のアクセラレータ キーのプロパティを変更するには

1. アイコンをダブルクリックして、アクセラレータ テーブルを開く[リソース ビュー](how-to-create-a-resource-script-file.md#create-resources)します。

1. 押しながら変更するアクセラレータ キーの選択、 **Ctrl**キーの 1 つを選択するとします。

1. 移動して、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)し、すべて、選択したアクセラレータを共有するのに必要な値を入力します。

> [!NOTE]
> ブール型プロパティとして各修飾子の値が表示されます、**プロパティ**ウィンドウ。 変更した場合、[修飾子](../windows/accelerator-modifier-property.md)値、**プロパティ**ウィンドウで、アクセラレータ テーブルで、れていた、修飾子の追加として新しい修飾子が扱われます。 このため、任意の修飾子の値を設定するとする必要がありますすべて同じすべてのアクセラレータを共有することを確認するよう設定**修飾子**設定します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[リソース エディター](../windows/resource-editors.md)<br/>
[アクセラレータ キー](../windows/predefined-accelerator-keys.md)<br/>