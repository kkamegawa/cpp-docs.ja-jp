---
title: /Qpar-report (自動並行化レポート作成レベル)
ms.date: 11/04/2016
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
ms.openlocfilehash: 25732900fa201258331dcb8eee96af9ba97a6def
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319955"
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-report (自動並行化レポート作成レベル)

コンパイラのレポート機能を有効に[自動並行化](../../parallel/auto-parallelization-and-auto-vectorization.md)し、コンパイル時に出力の情報メッセージのレベルを指定します。

## <a name="syntax"></a>構文

```
/Qpar-report:{1}{2}
```

## <a name="remarks"></a>Remarks

**/Qpar-レポート: 1**<br/>
並列化されたループに対する情報メッセージを出力します。

**/Qpar-レポート: 2**<br/>
並列化されたループと並列化されていないループの情報メッセージを理由コードと共に出力します。

メッセージは stdout に報告されます。 情報メッセージが報告されない場合、コードにループが含まれていないか、並列化されていないループが報告されるようにレポートのレベルが設定されていませんでした。 理由コードとメッセージの詳細については、次を参照してください。[ベクター化と並行化メッセージ](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)します。

### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>/Qpar-report コンパイラ オプションを Visual Studio で設定するには

1. **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、 **[プロパティ]** をクリックします。

1. **プロパティ ページ**ダイアログ ボックスで、 **C/C++**、**コマンド ライン**。

1. **追加オプション**ボックスに、入力`/Qpar-report:1`または`/Qpar-report:2`します。

### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>/Qpar-report コンパイラ オプションをコードから設定するには

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> のコード例を使用してください。

## <a name="see-also"></a>関連項目

[/Q オプション (低水準の操作)](q-options-low-level-operations.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[ネイティブ コードでの並列プログラミング](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)
