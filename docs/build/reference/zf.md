---
title: /Zf (高速の PDB の生成)
ms.date: 03/29/2018
f1_keywords:
- /Zf
helpviewer_keywords:
- /Zf
- -Zf
ms.openlocfilehash: bed37a189e3eb1eb7b55dbdee1f81f360eafa721
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315851"
---
# <a name="zf-faster-pdb-generation"></a>/Zf (高速の PDB の生成)

Mspdbsrv.exe への RPC 呼び出しを最小限に抑えることが並行ビルドでの高速の PDB 生成を有効にします。

## <a name="syntax"></a>構文

> **/Zf**

## <a name="remarks"></a>Remarks

**/Zf**オプションを使用する場合の PDB ファイルの生成を高速のコンパイラ サポートを有効に、 [/MP (複数のプロセスを使用したビルド)](mp-build-with-multiple-processes.md)オプション、またはビルド システム (たとえば、 [MSBuild](/visualstudio/msbuild/msbuild-reference)または[CMake](../cmake-projects-in-visual-studio.md)) が複数の cl.exe コンパイラ プロセス実行と同時にします。 このオプションは、コンパイルの最後までの PDB ファイルに各タイプのレコードの種類のインデックスの生成を遅延するには、コンパイラ フロント エンドと、し、mspdbsrv.exe、レコードごとに、RPC 要求ではなく、単一の RPC 呼び出しすべてでそれらを要求します。 ビルドのスループットは、複数の cl.exe コンパイラ プロセスが同時に実行環境で mspdbsrv.exe プロセスの RPC の負荷を減らすことでこの大幅向上できます。

**/Zf**オプションは、PDB の生成にのみ適用されますが必要です、 [/Zi](z7-zi-zi-debug-information-format.md)または[/ZI](z7-zi-zi-debug-information-format.md)オプション。

**/Zf**オプションは、既定でオフが以降では、Visual Studio 2017 バージョン 15.1 で使用できます。 以降では、Visual Studio 2017 バージョン 15.7 Preview 3 では、このオプションは既定でときに、 **/Zi**または **/ZI**オプションを有効にします。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **コマンドライン**プロパティ ページ。

1. 変更、**追加オプション**含めるプロパティを **/Zf**選び、 **OK**します。

## <a name="see-also"></a>関連項目

[アルファベット順のコンパイラ オプション](compiler-options-listed-alphabetically.md)<br/>
[/MP (複数のプロセスを使用したビルド)](mp-build-with-multiple-processes.md)<br/>
