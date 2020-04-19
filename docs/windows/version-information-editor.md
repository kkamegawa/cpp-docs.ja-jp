---
title: バージョン情報エディター (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.version.F1
- vc.editors.version
helpviewer_keywords:
- Version Information editor [C++], about Version Information editor
- editors, Version Information
- resource editors [C++], Version Information editor
- version information resources [C++]
- resources [C++], editing version information
- languages, version information
- New Version Info Block
- blocks, adding
- resources [C++], adding version information
- version information, adding for languages
- blocks, deleting
- version information, deleting blocks
- resources [C++], deleting version information
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
ms.openlocfilehash: e68e1480d2cd9a8d8a4d862252e6eb4384a5cd68
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513641"
---
# <a name="version-information-editor-c"></a>バージョン情報エディター (C++)

バージョン情報は、製造元および製品の識別情報、製品のリリース番号、著作権と商標の通知で構成されます。 **バージョン情報エディター**では、このデータを作成して管理します。このデータは、バージョン情報リソースに格納されます。 バージョン情報リソースはアプリケーションでは必要ありませんが、アプリケーションを識別する情報を収集するのに便利な場所です。 バージョン情報はセットアップ API でも使用されます。

> [!NOTE]
> Windows 標準では、VS_VERSION_INFO という名前のバージョン リソースが 1 つだけあります。

バージョン情報リソースには、1 つの上位ブロックと 1 つ以上の下位ブロックがあります。つまり、固定された情報ブロックが上部に 1 つと、バージョン情報ブロックが下部に 1 つ以上 (他の言語や文字セット用) あります。 上部のブロックには、編集可能な数字のボックスと選択可能なドロップダウン リストの両方があります。 下位ブロックには、編集可能なテキスト ボックスだけがあります。

> [!NOTE]
> **バージョン情報エディター**を使用しているときに、多くの場合、右クリックすると、リソース固有のコマンドのショートカットメニューが表示されます。 たとえば、ブロックヘッダーエントリをポイントしているときにを選択した場合、ショートカットメニューには、**新しいバージョンのブロック情報**と**削除バージョンブロック情報**コマンドが表示されます。

## <a name="how-to"></a>方法

**バージョン情報エディター**では、次のことが可能です。

### <a name="to-edit-a-string-in-a-version-information-resource"></a>バージョン情報リソースの文字列を編集するには

項目を1回選択して選択し、もう一度選択して編集を開始します。 **バージョン情報**テーブルまたは[プロパティウィンドウ](/visualstudio/ide/reference/properties-window)で直接変更を行います。 加えた変更は、両方の場所で反映されます。

`FILEFLAGS` **バージョン情報エディター**でキーを編集するときに、.rc ファイルの **[プロパティ]** ウィンドウで**デバッグ**、**プライベートビルド**、または**特別なビルド**プロパティを設定できないことに注意してください。

   - **バージョン情報エディター**は、 `_DEBUG`ビルドフラグに基づいて`#ifdef` 、リソーススクリプト内のを使用して**デバッグ**プロパティを設定します。

  - `FILEFLAGS`キーのバージョン情報テーブルに値が設定されている場合、キーの [プロパティ] ウィンドウで対応するプライベートビルドプロパティは True になります。 `Private Build` **値**が空の場合、プロパティは**False**になります。 同様に、**バージョン情報**テーブルの**特殊なビルド**キーは、 `FILEFLAGS`キーの**特別なビルド**プロパティに関連付けられています。

**キー**または**値**の列見出しを選択すると、文字列ブロックの情報シーケンスを並べ替えることができます。 これらの見出しは、選択した順序に情報を自動的に再配置します。

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>別の言語のバージョン情報を追加するには (新しいバージョン情報ブロック)

1. [[リソース ビュー]](how-to-create-a-resource-script-file.md#create-resources)でバージョン情報リソースをダブルクリックして開きます。

1. バージョン情報テーブル内を右クリックし、 **[新しいバージョン情報ブロック]** を選択します。

   このコマンドを使用して、現在のバージョン情報リソースにさらに情報ブロックを追加し、それに対応するプロパティを [[プロパティ] ウィンドウ](/visualstudio/ide/reference/properties-window)で開きます。

1. **[プロパティ]** ウィンドウで、新しいブロック用の適切な言語と文字セットを選びます。

### <a name="to-delete-a-version-information-block"></a>バージョン情報ブロックを削除するには

1. [[リソース ビュー]](how-to-create-a-resource-script-file.md#create-resources)でバージョン情報リソースのアイコンをダブルクリックして開きます。

1. 削除するブロックヘッダーを右クリックし、 **[バージョン情報ブロックの削除]** を選択します。

   このコマンドを実行すると、選択したヘッダーが削除され、残りのバージョン情報はそのまま残ります。 操作を元に戻すことはできません。

### <a name="to-access-version-information-from-within-your-program"></a>プログラム内からバージョン情報にアクセスするには

プログラム内からバージョン情報にアクセスする場合は、 [GetFileVersionInfo](/windows/win32/api/winver/nf-winver-getfileversioninfow) 関数と [VerQueryValue](/windows/win32/api/winver/nf-winver-verqueryvaluew) 関数を使用します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[リソース エディター](../windows/resource-editors.md)<br/>
[メニューとその他のリソース](/windows/win32/menurc/resources)<br/>
[バージョン情報 (Windows)](/windows/win32/menurc/version-information)
