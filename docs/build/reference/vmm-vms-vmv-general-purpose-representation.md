---
title: /vmm、-vms、-vmv (一般的な目的の表現)
ms.date: 11/04/2016
f1_keywords:
- /vms
- /vmm
- /vmv
helpviewer_keywords:
- Virtual Inheritance compiler option
- general purpose representation compiler options
- vms compiler option [C++]
- vmm compiler option [C++]
- /vmm compiler option [C++]
- -vmm compiler option [C++]
- -vms compiler option [C++]
- /vms compiler option [C++]
- vmv compiler option [C++]
- /vmv compiler option [C++]
- Single Inheritance compiler option
- -vmv compiler option [C++]
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
ms.openlocfilehash: 7a46cecdbf96ad891ce218df4769a60590e562a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316731"
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm、/vms、/vmv (通常の最適化)

ときに使用される[/vmb、/vmg () を処理形式](vmb-vmg-representation-method.md)として選択されて、[表現メソッド](vmb-vmg-representation-method.md)します。 これらのオプションは、not まだ検出クラス定義の継承モデルを示します。

## <a name="syntax"></a>構文

```
/vmm
/vms
/vmv
```

## <a name="remarks"></a>Remarks

これらのオプションの説明を次の表に示します。

|オプション|説明|
|------------|-----------------|
|**/vmm**|多重継承を使用するいずれかを指定するには、クラスのメンバーへのポインターの最も一般的な表現を指定します。<br /><br /> 対応する[継承キーワード](../../cpp/inheritance-keywords.md)への引数と[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)は**multiple_inheritance**します。<br /><br /> この表現は、単一継承した場合よりも大きくなります。<br /><br /> メンバーへのポインターが宣言されているクラス定義の継承モデルが仮想の場合、コンパイラはエラーを生成します。|
|**/vms**|いない継承または単一継承のいずれかを使用していずれかを指定するには、クラスのメンバーへのポインターの最も一般的な表現を指定します。<br /><br /> 対応する[継承キーワード](../../cpp/inheritance-keywords.md)への引数と[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)は**single_inheritance**します。<br /><br /> これは、クラスのメンバーへのポインターの最小サイズの表現です。<br /><br /> メンバーへのポインターが宣言されているクラス定義の継承モデルが複数ある場合または仮想の場合、コンパイラ エラーが発生します。|
|**/vmv**|仮想継承を使用するいずれかを指定するには、クラスのメンバーへのポインターの最も一般的な表現を指定します。 ありません、エラーが発生し、既定値です。<br /><br /> 対応する[継承キーワード](../../cpp/inheritance-keywords.md)への引数と[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)は**virtual_inheritance**します。<br /><br /> このオプションは、大きいサイズのポインターおよびその他のオプションよりもポインターを解釈するコードを追加が必要です。|

これらの継承モデル オプションのいずれかを指定すると、そのモデルは、クラス後の継承の種類や前に、またはにポインターを宣言するかどうかに関係なく、クラス メンバーへのすべてのポインターに使用されます。 そのため、常に単一継承のクラスを使用する場合はサイズを小さくコードでコンパイルする **/vms**ただし、(ただし、最大のデータ表現) の最も一般的なケースを使用する場合は、コンパイル **。/vmv**します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. **[追加のオプション]** ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[/vmb、/vmg (処理形式)](vmb-vmg-representation-method.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
