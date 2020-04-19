---
title: /APPCONTAINER (UWP/Microsoft Store アプリ)
ms.date: 11/04/2016
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
ms.openlocfilehash: f7ab8cf1ce034580953fdf1403264e8ef3d3ff09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295119"
---
# <a name="appcontainer-microsoft-store-app"></a>/APPCONTAINER (Microsoft Store App)

リンカーがアプリ コンテナーで実行される必要がある実行可能イメージを生成するかどうかを指定します。

## <a name="syntax"></a>構文

```
/APPCONTAINER[:NO]
```

## <a name="remarks"></a>Remarks

既定では、/APPCONTAINER は無効になっています。

このオプションは、実行可能ファイルを変更し、appcontainer プロセス分離環境でアプリが実行される必要があるかどうかを示します。 Appcontainer 環境で実行する必要があるアプリの/APPCONTAINER を指定 — など、ユニバーサル Windows プラットフォーム (UWP) アプリまたは Windows Phone 8.x アプリ。 (オプションは設定に自動的に Visual Studio でテンプレートからユニバーサル Windows アプリを作成するときに)。デスクトップ アプリケーションでは、/APPCONTAINER:NO を指定するか、オプションを省略します。

/APPCONTAINER オプションは、Windows 8 で導入されました。

### <a name="to-set-this-linker-option-in-visual-studio"></a>このリンカー オプションを Visual Studio で設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[構成プロパティ]** ノードを展開します。

1. 展開、**リンカー**ノード。

1. 選択、**コマンドライン**プロパティ ページ。

1. **追加オプション**、入力`/APPCONTAINER`または`/APPCONTAINER:NO`します。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
