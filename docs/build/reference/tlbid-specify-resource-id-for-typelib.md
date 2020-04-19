---
title: /TLBID (タイプ ライブラリのリソース ID の指定)
ms.date: 11/04/2016
f1_keywords:
- /tlbid
- VC.Project.VCLinkerTool.TypeLibraryResourceID
helpviewer_keywords:
- tlb files, specifying resource ID
- -TLBID linker option
- .tlb files, specifying resource ID
- /TLBID linker option
- TLBID linker option
- type libraries, specifying resource ID
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
ms.openlocfilehash: c52bfb9e4b6d0e94cecb77c766ac9e82b52f1e66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317797"
---
# <a name="tlbid-specify-resource-id-for-typelib"></a>/TLBID (タイプ ライブラリのリソース ID の指定)

```
/TLBID:id
```

## <a name="arguments"></a>引数

*ID*<br/>
リンカーによって作成されたタイプ ライブラリのユーザー指定の値。 1 の既定のリソース ID をオーバーライドします。

## <a name="remarks"></a>Remarks

属性を使用するプログラムをコンパイルするときに、リンカーは、タイプ ライブラリを作成します。 リンカーでは、タイプ ライブラリを 1 のリソース ID を割り当てます。

このリソース ID は、いずれか、既存のリソースと競合している場合は、/TLBID で別の ID を指定できます。 渡すことができる値の範囲`id`は 1 ~ 65535 です。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**埋め込み IDL**プロパティ ページ。

1. 変更、 **TypeLib リソース ID**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
