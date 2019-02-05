---
title: アクセラレータ テーブル (C++) の編集
ms.date: 11/04/2016
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
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
ms.assetid: 56e24efb-d06b-4ed9-8915-1f99f725e247
ms.openlocfilehash: dfa0c26132378bcbe8a7f5203351134d91746aa7
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232176"
---
# <a name="editing-accelerator-tables-c"></a>アクセラレータ テーブル (C++) の編集

インプレース編集を直接アクセラレータ テーブルを編集する C++ プロジェクトで、**アクセラレータ**エディター。

以下の手順は、標準のプロパティ ページの使用を参照してください、ただし、インプレース編集とプロパティ ページのメソッドの両方にある同じ結果になります。 プロパティ ページを使用して、またはインプレース編集を使用して行われた変更は、アクセラレータ テーブルですぐに反映されます。

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

> [!NOTE]
> プロジェクトに .rc ファイルがまだ含まれていない場合は、「 [リソース スクリプト ファイルの新規作成](../windows/how-to-create-a-resource-script-file.md)」を参照してください。

## <a name="to-edit-in-an-accelerator-table"></a>アクセラレータ テーブルで編集するには

1. アイコンをダブルクリックして、アクセラレータ テーブルを開く[リソース ビュー](../windows/resource-view-window.md)します。

1. テーブルでエントリを選択し、インプレース編集をアクティブ化を選択します。

1. 変更するには、ドロップダウン コンボ ボックスから選択するか、インプレースで入力します。

   - [ID](id-property.md)でリストまたは入力して編集を選択します。

   - [修飾子](../windows/accelerator-modifier-property.md)を一覧から選択します。

   - [キー](../windows/accelerator-key-property.md)でリストまたは入力して編集を選択します。

   - [型](../windows/accelerator-type-property.md)、 **ASCII**または**VIRTKEY**一覧から。

## <a name="to-find-an-entry-in-an-open-accelerator-table"></a>開いているアクセラレータ テーブルでエントリを検索するには

1. アイコンをダブルクリックして、アクセラレータ テーブルを開く[リソース ビュー](../windows/resource-view-window.md)します。

1. 列の内容をアルファベット順に並べ替える列見出しを選択します。 たとえば、 **ID**アクセラレータ テーブル内のすべての Id をアルファベット順に表示します。

これで、一覧に目を通しながらエントリを探すことができます。

## <a name="to-add-an-entry-to-an-accelerator-table"></a>アクセラレータ テーブルにエントリを追加するには

1. アイコンをダブルクリックして、アクセラレータ テーブルを開く[リソース ビュー](../windows/resource-view-window.md)します。

1. アクセラレータ テーブル内で右クリックし、**新しいアクセラレータ**からショートカット メニューのまたはテーブルの下部にある空の行エントリを選択します。

1. 選択、 [ID](id-property.md) ID のドロップダウン リストからボックスまたは新しい ID を入力、 **ID**ボックス。

1. 型、[キー](../windows/accelerator-key-property.md)アクセラレータまたは右クリックとして使用する**キー タイピング登録**キーの組み合わせを設定するショートカット メニュー (、 **キー タイピング登録**コマンドは、使用可能な**編集**メニュー)。

1. 変更、[修飾子](../windows/accelerator-modifier-property.md)と[型](../windows/accelerator-type-property.md)、必要な場合。

1. **Enter** キーを押します。

   > [!NOTE]
   > 定義するすべてのアクセラレータが一意であることを確認します。 たとえば、同じ ID に割り当てられているいくつかのキーの組み合わせがあることができます**Ctrl** + **P**と**F8**どちらも ID_PRINT に割り当てる割り当てすることができます。 ただし、1 つ以上の ID は、うまく機能しませんなどに割り当てられているキーの組み合わせを持つ**Ctrl** + **Z** ID_SPELL_CHECK と ID_THESAURUS の両方に割り当てられます。

## <a name="to-delete-an-entry-from-an-accelerator-table"></a>アクセラレータ テーブルのエントリを削除するには

1. アイコンをダブルクリックして、アクセラレータ テーブルを開く[リソース ビュー](../windows/resource-view-window.md)します。

1. 削除するエントリを選択します (を押しながら、 **Ctrl**または**Shift**複数のエントリを選択することを選択するのにはキーです)。

1. 右クリックし、**削除**、ショートカット メニューから (または選択**削除**から、**編集**メニュー)。

\- または -

- キーを押して、**削除**キー。

## <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>アクセラレータ テーブルのエントリを別のリソース スクリプト ファイルに移動またはコピーするには

1. 両方のリソース スクリプト ファイルでアクセラレータ テーブルを開きます。

1. 移動するエントリを選択します。

1. **編集**] メニューの [選択**コピー**または**切り取り**します。

1. 移動先またはコピー先のリソース スクリプト ファイルでエントリを選択します。

1. **編集**] メニューの [選択**貼り付け**します。

   > [!NOTE]
   > コピーと貼り付けのショートカット キーも使用できます。

## <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>複数のアクセラレータ キーのプロパティを変更するには

1. アイコンをダブルクリックして、アクセラレータ テーブルを開く[リソース ビュー](../windows/resource-view-window.md)します。

1. 押しながら変更するアクセラレータ キーの選択、 **Ctrl**キーの 1 つを選択するとします。

1. 移動して、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)し、すべて、選択したアクセラレータを共有するのに必要な値を入力します。

   > [!NOTE]
   > ブール型プロパティとして各修飾子の値が表示されます、**プロパティ**ウィンドウ。 変更した場合、[修飾子](../windows/accelerator-modifier-property.md)値、**プロパティ**ウィンドウで、アクセラレータ テーブルで、れていた、修飾子の追加として新しい修飾子が扱われます。 このため場合は、修飾子の値を設定する必要がありますすべて同じすべてのアクセラレータを共有することを確認するを設定する**修飾子**設定します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[アクセラレータ エディター](../windows/accelerator-editor.md)<br/>
[リソース エディター](../windows/resource-editors.md)
