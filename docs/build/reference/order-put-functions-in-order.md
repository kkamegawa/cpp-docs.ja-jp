---
title: /ORDER (関数の順序)
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.FunctionOrder
- /order
helpviewer_keywords:
- ORDER linker option
- -ORDER linker option
- LINK tool [C++], program optimizing
- /ORDER linker option
- LINK tool [C++], swap tuning
- paging, optimizing
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
ms.openlocfilehash: b1927ffd2efc923157fe1956fe905c939bc62719
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320189"
---
# <a name="order-put-functions-in-order"></a>/ORDER (関数の順序)

(COMDAT) 関数を個別にパッケージのリンクの順序を指定します。

## <a name="syntax"></a>構文

> **/ORDER:\@**<em>ファイル名</em>

### <a name="parameters"></a>パラメーター

*ファイル名*<br/>
COMDAT 関数のリンクの順序を指定するテキスト ファイルです。

## <a name="remarks"></a>Remarks

**/Order**コンパイラ オプションでは、関数が呼び出す関数と関数をグループ化して、プログラムのページングの動作を最適化できます。 頻繁に呼び出される関数をまとめてグループすることもできます。 呼ばれるこれらの手法*スワップ調整*または*ページング最適化*、およびディスクからページングする必要はありませんが必要な時に、呼び出された関数がメモリ内の確率を高めます。

オブジェクト ファイルにソース コードをコンパイルするときと呼ばれる独自のセクションの各関数にコンパイラに通知することができます、 *COMDAT*を使用して、 [/Gy (関数レベルのリンクを有効にする)](gy-enable-function-level-linking.md)コンパイラオプション。 **/Order**リンカー オプション、リンカーは、指定した順序で実行可能イメージに Comdat を配置します。

COMDAT の順序を指定するには、作成、*応答ファイル*、リンカーによって配置される順序で行ごとに 1 つには、名前で各 COMDAT を一覧表示するテキスト ファイル。 としてこのファイルの名前を渡す、 *filename*のパラメーター、 **/order**オプション。 C++ 関数の場合、COMDAT の名前は、関数名の装飾形式です。 C# 関数では、非装飾名を使用して、 `main`、として宣言されている C++ 関数と`extern "C"`します。 関数名と装飾名は大文字小文字を区別します。 装飾名の詳細については、次を参照してください。[装飾名](decorated-names.md)します。

Comdat の装飾名を検索するには、使用、 [DUMPBIN](dumpbin-reference.md)ツールの[/symbols](symbols.md)オブジェクト ファイルのオプション。 リンカーは、アンダー スコアを自動的に付加 (**\_**) 関数に疑問符 () で始まる名前を応答で名ファイル (**でしょうか**) またはアット マーク ( **\@。**). たとえば、ソース ファイルでは、example.cpp、関数が含まれます`int cpp_func(int)`、`extern "C" int c_func(int)`と`int main(void)`のコマンドは、`DUMPBIN /SYMBOLS example.obj`これらの装飾名が表示されます。

```Output
...
088 00000000 SECT1A notype ()    External     | ?cpp_func@@YAHH@Z (int __cdecl cpp_func(int))
089 00000000 SECT22 notype ()    External     | _c_func
08A 00000000 SECT24 notype ()    External     | _main
...
```

ここと名前を指定`?cpp_func@@YAHH@Z`、 `c_func`、および`main`応答ファイルにします。

1 つ以上の場合 **/order**リンカー オプションのオプションが表示されたら、指定された最後の 1 つ有効になります。

**/Order**オプションは、インクリメンタル リンクを無効になります。 リンカー警告が表示される[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)インクリメンタル リンクが有効になっている場合、または指定した場合にこのオプションを指定する場合、 [/ZI (増分 PDB)](z7-zi-zi-debug-information-format.md)コンパイラ オプション。 この警告をミュートするには、使用することができます、 [/INCREMENTAL:NO](incremental-link-incrementally.md) 、インクリメンタル リンクをオフにして使用するリンカー オプション、 [/Zi (PDB の生成)](z7-zi-zi-debug-information-format.md)インクリメンタル リンクせず、PDB を生成するコンパイラ オプション。

> [!NOTE]
> 静的関数の名前は、パブリック シンボル名ではないために、リンクは静的関数を注文ことはできません。 ときに **/order**指定すると、リンカー警告[LNK4037](../../error-messages/tool-errors/linker-tools-warning-lnk4037.md)が静的か、見つかりません。 順序の応答ファイル内の各シンボルが生成されます。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **リンカー** > **最適化**プロパティ ページ。

1. 変更、**関数の順序**応答ファイルの名前を格納するプロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
