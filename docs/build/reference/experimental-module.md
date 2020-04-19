---
title: '/試験: モジュール (モジュールサポートの有効化)'
description: 'モジュールの試験的なコンパイラサポートを有効にするには、/実験的: module コンパイラオプションを使用します。'
ms.date: 09/03/2019
f1_keywords:
- module
- /experimental:module
helpviewer_keywords:
- module
- /experimental:module
- Enable module support
ms.openlocfilehash: 82cce127ad5a2f87d11e4a653035bd80ea9f5001
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294459"
---
# <a name="experimentalmodule-enable-module-support"></a>/試験: モジュール (モジュールサポートの有効化)

ドラフト C++ 20 標準で指定されているように、モジュールの実験的なコンパイラサポートを有効にします。

## <a name="syntax"></a>構文

> **/実験的: モジュール**[ **-** ]

## <a name="remarks"></a>Remarks

/**実験的: module**コンパイラオプションを[/std:c++ latest](std-specify-language-standard-version.md)オプションと共に使用することで、実験的なモジュールのサポートを有効にすることができます。 **/試験的な**モジュールを使用して、モジュールのサポートを明示的に無効にすることができます。

このオプションは、Visual Studio 2015 Update 1 以降で使用できます。 Visual Studio 2019 バージョン16.2 以降、Draft C++ 20 Standard モジュールは Microsoft C++コンパイラで完全には実装されていません。 モジュール機能を使用して、単一パーティションのモジュールを作成し、Microsoft が提供する標準ライブラリモジュールをインポートすることができます。 モジュールとそれを使用するコードは、同じコンパイラオプションを使用してコンパイルする必要があります。

モジュールの詳細および使用方法と作成方法については、「」の「 [ C++モジュールの概要](../../cpp/modules-cpp.md)」を参照してください。

ソースファイル ModuleName からエクスポートモジュールを作成するために使用されるコンパイラのコマンドラインオプションの例を次に示し*ます。 ixx*:

```cmd
cl /EHsc /MD /experimental:module /module:export /module:name ModuleName /module:wrapper C:\Output\path\ModuleName.h /module:output C:\Output\path\ModuleName.ifc -c ModuleName.ixx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[構成]** ドロップダウンを **[すべての構成]** に設定します。

1. [**構成プロパティ** > ] [**CC++/**  > **言語**] プロパティページを選択します。

1. **[モジュール ( C++試験段階) を有効にする]** プロパティを変更し、[ **OK]** をクリックします。

## <a name="see-also"></a>関連項目

[/Zc (準拠)](zc-conformance.md)
