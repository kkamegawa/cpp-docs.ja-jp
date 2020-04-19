---
title: /CLRTHREADATTRIBUTE (CLR スレッド属性の設定)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
ms.openlocfilehash: ad07c84a5c470cd5fa1ac10ff6d2baed5c35c025
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272469"
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE (CLR スレッド属性の設定)

CLR プログラムのエントリ ポイントにスレッド属性を明示的に指定します。

## <a name="syntax"></a>構文

```
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}
```

#### <a name="parameters"></a>パラメーター

**MTA**<br/>
MTAThreadAttribute 属性をプログラムのエントリ ポイントに適用されます。

**NONE**<br/>
/CLRTHREADATTRIBUTE を指定しないと同じです。  既定のスレッド属性を設定する共通言語ランタイム (CLR) を使用できます。

**STA**<br/>
STAThreadAttribute 属性をプログラムのエントリ ポイントに適用されます。

## <a name="remarks"></a>Remarks

スレッド属性設定のみ有効です、.exe を構築するときに、メイン スレッドのエントリ ポイントに影響するため。

使用する場合は、(main または wmain の例では、)、既定のエントリ ポイント指定スレッド処理モデルを/CLRTHREADATTRIBUTE を使用するかまたは配置することで、スレッド処理属性 (STAThreadAttribute または MTAThreadAttribute) を既定のエントリ関数。

既定以外のエントリ ポイントを使用する場合は、/CLRTHREADATTRIBUTE を使用するか、スレッドを配置することで、既定以外のエントリ関数で属性し、既定以外のエントリ ポイントを指定し、スレッド処理モデルを指定[/ENTRY](entry-entry-point-symbol.md).

ソース コードで指定されたスレッド処理モデルは、/CLRTHREADATTRIBUTE で指定されたスレッド モデルと一致しません、リンカーは/CLRTHREADATTRIBUTE を無視し、ソース コードで指定されたスレッド処理モデルを適用します。

CLR プログラムは、シングル スレッドを使用する COM オブジェクトをホストしている場合は、シングル スレッドを使用するために必要になります。  マルチ スレッドを使用する CLR プログラム場合、シングル スレッドを使用する COM オブジェクトをホストできません。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[構成プロパティ]** ノードを展開します。

1. 展開、**リンカー**ノード。

1. 選択、**詳細**プロパティ ページ。

1. 変更、 **CLR スレッド属性の**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
