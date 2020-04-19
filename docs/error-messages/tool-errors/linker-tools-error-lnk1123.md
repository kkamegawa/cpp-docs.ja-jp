---
title: リンカ ツール エラー LNK1123
ms.date: 12/29/2017
f1_keywords:
- LNK1123
helpviewer_keywords:
- LNK1123
ms.openlocfilehash: 31fd634291bfb0af17348197ae8a6225ac490c89
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509904"
---
# <a name="linker-tools-error-lnk1123"></a>リンカ ツール エラー LNK1123

> COFF への変換中に障害が発生しました : ファイルが無効であるか、または壊れています。

入力ファイルは、COFF (Common Object File Format) 形式である必要があります。 入力ファイルが COFF でない場合、リンカーによって 32 ビット OMF オブジェクトが COFF に自動変換されるか、リソース ファイルを変換するための CVTRES.EXE が実行されます。 このメッセージは、リンカーがファイルを変換できなかったことを示します。 これは、Visual Studio、Windows Development Kit、または .NET Framework の別のインストールから CVTRES.EXE の非互換バージョンを使用している場合にも発生します。

> [!NOTE]
> 旧バージョンの Visual Studio を実行している場合は、自動変換がサポートされない場合があります。

## <a name="to-fix-the-problem"></a>この問題を解決するには、次のいずれかを行います。

- Visual Studio の該当するバージョン用のすべての更新プログラムとサービス パックを適用します。 これは、Visual Studio 2010年には特に重要です。

- インクリメンタル リンクを無効にしてビルドしてみます。 メニュー バーで、 **[プロジェクト]** 、 **[プロパティ]** の順に選びます。 [**プロパティページ**] ダイアログボックスで、[**構成プロパティ**]、[**リンカー**] の順に展開します。 [**インクリメンタルリンクを有効**にする] の値を [**いいえ**] に変更します。

- PATH 環境変数で最初に見つかる CVTRES.EXE のバージョンが、プロジェクトで使用されるビルド ツールのバージョン (プラットフォーム ツールセットのバージョン) と一致することを確認します。

- [埋め込みマニフェスト] のオプションをオフにしてください。 メニュー バーで、 **[プロジェクト]** 、 **[プロパティ]** の順に選びます。 [**プロパティページ**] ダイアログボックスで、 **[構成プロパティ**]、[**マニフェストツール**]、[**入力および出力**] の順に展開します。 **埋め込みマニフェスト**の値を **いいえ (いいえ**) に変更します。

- ファイルの種類が有効であることを確認します。 たとえば OMF オブジェクトが 16 ビットではなく 32 ビットであることを確認します。 詳細については、「」を参照してください[。リンカー入力](../../build/reference/dot-obj-files-as-linker-input.md)および[PE 形式](/windows/win32/Debug/pe-format)としての Obj ファイル。

- ファイルが破損していないことを確認してください。 必要に応じて再構築します。

## <a name="see-also"></a>関連項目

[.obj ファイル (リンカー入力)](../../build/reference/dot-obj-files-as-linker-input.md)<br/>
[EDITBIN リファレンス](../../build/reference/editbin-reference.md)<br/>
[DUMPBIN リファレンス](../../build/reference/dumpbin-reference.md)
