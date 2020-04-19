---
title: /NOPDB
description: /NOPDB オプションを使用すると、DUMPBIN がシンボル情報の PDB ファイルを読み込んで検索することができます。
ms.date: 12/04/2019
f1_keywords:
- /NOPDB
helpviewer_keywords:
- /NOPDB dumpbin option
- /NOPDB
ms.openlocfilehash: 7b0c01e59b52bcec6ddf09416dd6aac9999527a6
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856970"
---
# <a name="nopdb"></a>/NOPDB

シンボル情報のプログラムデータベース (PDB) ファイルを読み込まないように DUMPBIN に指示します。

## <a name="syntax"></a>構文

> **/NOPDB**

## <a name="remarks"></a>Remarks

既定では、DUMPBIN はターゲットの実行可能ファイルの PDB ファイルを読み込もうとします。 DUMPBIN は、この情報を使用して、アドレスをシンボル名に一致させます。 PDB ファイルのサイズが大きい場合、またはリモートサーバーから読み込む必要がある場合は、処理に時間がかかることがあります。 **/NOPDB**オプションは、この手順をスキップするよう DUMPBIN に指示します。 実行可能ファイルで使用可能なアドレスとシンボル情報のみが出力されます。

### <a name="to-set-the-nopdb-linker-option-in-visual-studio"></a>Visual Studio で/NOPDB リンカーオプションを設定するには

1. プロジェクトの **[プロパティページ]** ダイアログボックスを開きます。 詳しくは、「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](../working-with-project-properties.md)」をご覧ください。

1. **[構成プロパティ]**  >  **[リンカー]**  >  **[コマンド ライン]** プロパティ ページを選択します。

1. **[追加オプション]** ボックスで、 **/NOPDB**オプションを追加します。 **[OK]** または **[適用]** を選択して、変更を保存します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- このオプションには、プログラムに相当するものはありません。

## <a name="see-also"></a>参照

[DUMPBIN コマンドライン](dumpbin-command-line.md)\
[DUMPBIN オプション](dumpbin-options.md)\
[DUMPBIN リファレンス](dumpbin-reference.md)
