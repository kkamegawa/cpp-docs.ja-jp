---
title: /Zp (構造体メンバーの配置)
ms.date: 12/17/2018
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
ms.openlocfilehash: d1821d8dc5eab202a918893a1e7895151629b551
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627528"
---
# <a name="zp-struct-member-alignment"></a>/Zp (構造体メンバーの配置)

メモリに構造体のメンバーをパックする方法を制御し、モジュール内のすべての構造の同じパッキングを指定します。

## <a name="syntax"></a>構文

> **/Zp**[**1**|**2**|**4**|**8** | **16**]

## <a name="remarks"></a>Remarks

指定した場合、 **/Zp**_n_オプションを 1 つ目がメンバーの種類のサイズのどちらかに格納されている各構造体メンバーまたは*n*-バイト境界 (場所*n*が 1、2、4、8、または 16)、小さい方です。

パッキングの使用可能な値は、次の表で説明します。

|/Zp 引数|効果|
|-|-|
|1|構造体は、1 バイト境界でパックします。 同じ **/Zp**します。|
|2|構造体を 2 バイト境界でパックします。|
|4|構造体は、4 バイト境界でパックします。|
|8|8 バイト境界 (既定値) の構造体にパックします。|
|16| 構造体を 16 バイト境界でパックします。|

特定のアラインメント要件がない限りは、このオプションを使用する必要があります。

> [!WARNING]
> Windows SDK の C++ ヘッダーと **、/zp8 です**梱包です。 メモリの破損が生じる場合、 **/Zp** Windows SDK のヘッダーを使用する場合、設定を変更します。

使用することも[パック](../../preprocessor/pack.md)制御構造のパッキングにします。 アラインメントの詳細については、次のトピックを参照してください。

- [align](../../cpp/align-cpp.md)

- [__alignof 演算子](../../cpp/alignof-operator.md)

- [__unaligned](../../cpp/unaligned.md)

- [構造体の配置例](../../build/x64-software-conventions.md#examples-of-structure-alignment)(x64 固有)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. 選択、 **C/C++** > **コード生成**プロパティ ページ。

1. 変更、**構造体メンバーのアラインメント**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>

## <a name="see-also"></a>関連項目

- [コンパイラ オプション](../../build/reference/compiler-options.md)
- [コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)
