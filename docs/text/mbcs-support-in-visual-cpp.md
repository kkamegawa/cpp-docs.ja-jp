---
title: Visual C++ における MBCS のサポート
ms.date: 11/04/2016
helpviewer_keywords:
- tools [C++], MBCS support
- Asian languages [C++]
- Code Editor [C++], MBCS support
- IME [C++]
- Chinese characters [C++]
- Input Method Editor [C++], MBCS
- resource editors [C++], MBCS support
- debugger [C++], MBCS support
- character sets [C++], multibyte
- Japanese characters [C++]
- multibyte characters [C++]
- Kanji character support [C++]
- NMAKE program, MBCS support
- double-byte character sets [C++]
- IME [C++], MBCS
- Input Method Editor [C++]
- MBCS [C++], enabling
ms.assetid: 6179f6b7-bc61-4a48-9267-fb7951223e38
ms.openlocfilehash: b5f2b6dd56d3a755ee73058c024152e12157a6bd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501944"
---
# <a name="mbcs-support-in-visual-c"></a>Visual C++ における MBCS のサポート

MBCS が有効になっているバージョンの Windows で実行するC++場合、ビジュアル開発システム (統合ソースコードエディター、デバッガー、およびコマンドラインツールを含む) は mbcs で有効ですが、[メモリ] ウィンドウは例外です。

[メモリ] ウィンドウでは、データを ANSI または Unicode 文字として解釈できる場合でも、データのバイトは MBCS 文字として解釈されません。 ANSI 文字のサイズは常に1バイトで、Unicode 文字のサイズは2バイトです。 MBCS では、文字数は1または2バイトで、その解釈は使用中のコードページによって異なります。 このため、[メモリ] ウィンドウで MBCS 文字を確実に表示することは困難です。 [メモリ] ウィンドウは、どのバイトが文字の先頭であるかを認識できません。 開発者は、[メモリ] ウィンドウでバイト値を表示し、テーブルの値を参照して文字表現を決定できます。 これが可能なのは、開発者がソースコードに基づいて文字列の開始アドレスを知っているためです。

ビジュアルC++では、そのために適切な場所に2バイト文字を指定できます。 これには、ダイアログボックス内のパス名とファイル名、およびビジュアルC++リソースエディターのテキストエントリ (たとえば、ダイアログエディターの静的テキストとアイコンエディターの静的テキストエントリ) が含まれます。 また、プリプロセッサは、ステートメント内`#include`のファイル名や`data_seg`プラグマの`code_seg`引数として、いくつかの2バイトディレクティブを認識します。 ソースコードエディターでは、C/C++言語要素 (変数名など) ではなく、コメントおよび文字列リテラル内の2バイト文字が許容されます。

##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>入力方式エディター (IME) のサポート

MBCS (たとえば日本) を使用する東アジア市場向けに作成されたアプリケーションでは、通常、1バイト文字と2バイト文字の両方を入力するための Windows IME がサポートされています。 ビジュアルC++開発環境には、IME の完全なサポートが含まれています。

日本語のキーボードは、漢字を直接サポートしていません。 IME は、他の日本語のアルファベット (Romaji、カタカナ、ひらがな) のいずれかに入力された発音文字列を、可能な漢字表現に変換します。 あいまいさがある場合は、いくつかの代替手段から選択できます。 目的の漢字文字を選択すると、IME は制御アプリケーション`WM_CHAR`に2つのメッセージを渡します。

ALT +\`キーの組み合わせによってアクティブ化される IME は、一連のボタン (インジケーター) と変換ウィンドウとして表示されます。 アプリケーションは、テキストの挿入ポイントにウィンドウを配置します。 アプリケーションでは、 `WM_MOVE`ターゲット`WM_SIZE`ウィンドウの新しい位置またはサイズに合わせて変換ウィンドウを再配置することによって、メッセージとメッセージを処理する必要があります。

アプリケーションのユーザーが漢字の文字を入力できるようにするには、アプリケーションで Windows IME メッセージを処理する必要があります。 IME プログラミングの詳細については、「 [Input Method Manager](/windows/win32/intl/input-method-manager)」を参照してください。

## <a name="visual-c-debugger"></a>ビジュアルC++デバッガー

Visual C++デバッガーには、IME メッセージにブレークポイントを設定する機能が用意されています。 さらに、[メモリ] ウィンドウには2バイト文字が表示されます。

## <a name="command-line-tools"></a>コマンド ライン ツール

コンパイラ、 C++ NMAKE、リソースコンパイラ (RC など) を含む、Visual コマンドラインツール。EXE) は、MBCS が有効になっています。 リソースコンパイラの/c オプションを使用して、アプリケーションのリソースをコンパイルするときに既定のコードページを変更できます。

ソースコードのコンパイル時に既定のロケールを変更するには、 [#pragma setlocale](../preprocessor/setlocale.md)を使用します。

## <a name="graphical-tools"></a>グラフィックツール

Spy + C++ + やリソース編集ツールなどのビジュアルな Windows ベースのツールは、IME 文字列を完全にサポートしています。

## <a name="see-also"></a>関連項目

[マルチバイト文字セット (MBCS) のサポート](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[MBCS のプログラミングについて](../text/mbcs-programming-tips.md)
