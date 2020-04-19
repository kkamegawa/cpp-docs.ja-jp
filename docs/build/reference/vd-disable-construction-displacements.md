---
title: /vd (ディスプレイスメントの無効化)
ms.date: 11/04/2016
f1_keywords:
- /vd
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
ms.openlocfilehash: db198dbdc7bd43ffd4de9bde39ee81a8b95a25ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316887"
---
# <a name="vd-disable-construction-displacements"></a>/vd (ディスプレイスメントの無効化)

## <a name="syntax"></a>構文

```
/vdn
```

## <a name="arguments"></a>引数

**0**<br/>
Vtordisp コンストラクター/デストラクター ディスプレイスメント メンバーを使用すると、抑制します。 すべてのクラスのコンス トラクターとデストラクターが仮想呼び出すことがわかっている場合にのみ、このオプションは事実上関数を選択します。

**1**<br/>
隠し vtordisp コンストラクター/デストラクター ディスプレイスメント メンバーを作成をできます。 このオプションは、既定値です。

**2**<br/>
使用できるように[dynamic_cast Operator](../../cpp/dynamic-cast-operator.md)で構築されるオブジェクト。 たとえば、仮想基底クラスから派生クラスへの dynamic_cast です。

**/vd2**仮想関数を持つ仮想基底がある場合は、vtordisp フィールドを追加します。 **/vd1**十分です。 最も一般的なケース **/vd2**が必要なは、仮想ベースで唯一の仮想関数がデストラクターの場合。

## <a name="remarks"></a>Remarks

これらのオプションは、仮想基底クラスを使用する C++ コードにのみ適用されます。

Visual C では、仮想継承を使用する状況で C++ ディスプレイスメントをサポートを実装します。 ディスプレイスメントは仮想関数の場合、仮想ベースで宣言され、派生クラスでオーバーライドされるときに作成の問題を解決、さらに派生クラスの構築中にコンス トラクターから呼び出されます。

問題は仮想関数が不適切な渡される可能性があります、`this`ポインター、結果として、仮想変位の不一致の基底クラスとその派生クラスにします。 ソリューションでは、各仮想基本クラスの vtordisp フィールドと呼ばれる 1 つ構築変位の調整を提供します。

既定では、vtordisp フィールドは、コードは、ユーザー定義のコンス トラクターとデストラクターを定義し、仮想基底クラスの仮想関数がオーバーライドされるたびに導入されました。

これらのオプションでは、ソース ファイル全体に影響します。 使用[vtordisp](../../preprocessor/vtordisp.md)を抑制しクラスによって単位で vtordisp フィールドを再度有効にします。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. **[追加のオプション]** ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
