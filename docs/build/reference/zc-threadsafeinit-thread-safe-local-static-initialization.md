---
title: '/Zc: threadsafeinit (スレッド セーフなローカル静的な初期化)'
ms.date: 03/14/2018
f1_keywords:
- threadSafeInit
- /Zc:threadSafeInit
helpviewer_keywords:
- -Zc compiler options (C++)
- threadSafeInit
- Thread-safe Local Static Initialization
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: a0fc4b34-2cf0-45a7-a642-b8afc4ca19f2
ms.openlocfilehash: 92a1bfa5ec3bab2814397d51e35e617b7666c706
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315704"
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/Zc: threadsafeinit (スレッド セーフなローカル静的な初期化)

**/Zc: threadsafeinit**コンパイラ オプションで、スレッド セーフな方法、手動で同期する必要がなくなります (関数スコープ) の静的ローカル変数を初期化するためにコンパイラに指示します。 のみの初期化とは、スレッド セーフです。 使用して複数のスレッドによる静的ローカル変数を変更する必要がありますも手動で同期します。 このオプションは、Visual Studio 2015 以降で使用できます。 既定では、Visual Studio は、このオプションを有効します。

## <a name="syntax"></a>構文

> **/Zc:threadSafeInit**[**-**]

## <a name="remarks"></a>Remarks

C++ 11 標準で静的ではブロック スコープ変数またはスレッド ストレージ存続期間必要があります 0 で初期化する他の初期化が行われる前にします。 初期化は、コントロールは、まず、変数の宣言を通過するときに発生します。 初期化中に例外がスローされた場合は、変数は、初期化されていないと見なされますの初期化が再実行しようとした時間の次のコントロール宣言を通過します。 コントロールは、宣言、初期化が完了したときに、同時実行要素の初期化と同時になります。 場合、 コントロールの初期化中に、宣言の再帰的に再入力した場合、動作は未定義です。 既定では、Visual Studio の Visual Studio 2015 以降では、この標準の動作を実装します。 この動作を設定して明示的に指定することがあります、 **/zc: threadsafeinit**コンパイラ オプション。

**/Zc: threadsafeinit**コンパイラ オプションが既定でオンです。 [/Permissive -](permissive-standards-conformance.md)オプションには影響しません **/zc: threadsafeinit**します。

静的ローカル変数のスレッド セーフな初期化は、ユニバーサル C ランタイム ライブラリ (UCRT) で実装されるコードに依存します。 UCRT に依存することを回避するために、または Visual Studio 2015 より前の Visual Studio のバージョンの非スレッド セーフな初期化の動作を保持するには、使用、 **/Zc:threadSafeInit-** オプション。 そのスレッドの安全性が必要でない場合は、静的ローカル宣言の周囲に若干小さく、高速なコードを生成するこのオプションを使用します。

スレッド セーフな静的ローカル変数、静的なは既に初期化された後に効率的に実行を提供するのにスレッド ローカル ストレージ (TLS) を内部的に使用します。 この機能の実装は、Windows Vista 以降のオペレーティング システムでの Windows オペレーティング システムのサポート機能に依存します。 Windows XP、Windows Server 2003、および以前のオペレーティング システムでは効率のメリットが得られないため、このサポートを必要ことはありません。 これらのオペレーティング システムでは、読み込むことができる TLS セクションの数に制限を設けるもあります。 TLS を超えると制限のセクションではクラッシュが発生ことができます。 これは、以前のオペレーティング システムで実行するコードには特に、コードの問題がある場合は、使用 **/Zc:threadSafeInit-** スレッド セーフな初期化コードを無効にします。

Visual C++ の準拠に関する問題について詳しくは、「 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)」をご覧ください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **構成**ドロップダウン メニューで、**すべて構成**します。

1. 選択、**構成プロパティ** > **C/C++** > **コマンドライン**プロパティ ページ。

1. 変更、**追加オプション**含めるプロパティを **/zc: threadsafeinit**または **/Zc:threadSafeInit-** 選び、 **OK**します。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[/Zc (準拠)](zc-conformance.md)<br/>
