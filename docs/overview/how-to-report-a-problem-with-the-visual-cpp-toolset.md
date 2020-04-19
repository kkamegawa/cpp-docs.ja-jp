---
title: Microsoft C++ ツールセットで問題を報告する方法
description: Microsoft C++ ツールセットに関して適切な問題レポートを作成する方法と情報を再現する方法
ms.date: 09/24/2019
ms.technology: cpp-ide
author: corob-msft
ms.author: corob
ms.openlocfilehash: 350e902501aca5cbe2b4022ec1f977719844644b
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685702"
---
# <a name="how-to-report-a-problem-with-the-microsoft-c-toolset-or-documentation"></a>Microsoft C++ ツールセットまたはドキュメントの問題を報告する方法

Microsoft C++ コンパイラ (MSVC)、リンカー、またはその他のツールやライブラリで問題が見つかった場合は、それらをお知らせください。 ドキュメントに問題がある場合は、そちらもお知らせください。

## <a name="how-to-report-a-c-toolset-issue"></a>Visual C++ ツールセットの問題を報告する方法

問題についてお知らせいただく最善の方法は、お客様が発見された問題の説明を含むレポートを送ることです。 プログラムをビルドした方法についての詳細がすべて含まれる必要があります。 また、弊社のコンピューターで問題を再現するために使用できる完全なテスト ケースである "*再現コード*" も含まれる必要があります。 この情報を使用して、問題は弊社のコード内に存在しており、お客様の環境に固有のものではないことを迅速に確認できます。 他のバージョンのコンパイラに影響を与えるかどうかを特定し、原因を診断するのに役立ちます。

以下のセクションでは、よいレポートの特長について説明します。 発見した問題の再現コードの生成方法、製品チームへのレポートの送信方法について説明します。 レポートは、Microsoft にとっても他の開発者にとっても重要です。 Microsoft C++ の向上にご協力いただきありがとうございます。

## <a name="how-to-prepare-your-report"></a>レポートを準備する方法

完全な情報がないとお客様が発見した問題を弊社で再現することが難しいため、適切なレポートを作成することが重要です。 レポートの質がよいほど、より効果的に問題を再現して診断できます。

レポートには少なくとも次の情報を含める必要があります。

- 使っているツールセットの完全なバージョン情報。

- コードをビルドするために使った完全な cl.exe コマンド ライン。

- 発生した問題の詳細な説明。

- 再現コードは、問題を実際に示す完全な簡素化された自己完結型のソース コード例です。

具体的に必要な情報およびそれが見つかる場所、および最適な再現コードの作成方法については以下で説明します。

### <a name="the-toolset-version"></a>ツールセットのバージョン

問題の原因であるツールセットの完全なバージョン情報とターゲット アーキテクチャが必要です。 適切であれば、弊社のコンピューターで同じツールセットに対して再現コードをテストすることができます。 問題を再現できる場合、この情報を基にして同じ問題が発生するツールセットの他のバージョンを調査できます。

#### <a name="to-report-the-full-version-of-your-compiler"></a>お使いのコンパイラの完全なバージョンを報告するには

1. プロジェクトをビルドするために使用した Visual Studio のバージョンと構成アーキテクチャに一致する**開発者コマンド プロンプト**を開きます。 たとえば、x64 ターゲットに対して、x64 で Visual Studio 2017 を使用してビルドする場合は、**VS 2017 用の x64 Native Tools コマンド プロンプト**を選びます。 詳細については、[開発者コマンド プロンプトのショートカット](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)に関するトピックを参照してください。

1. 開発者コマンド プロンプト コンソール ウィンドウで、コマンド **cl /Bv** を入力します。

出力は次のようになります。

```Output
C:\Users\username\Source>cl /Bv
Microsoft (R) C/C++ Optimizing Compiler Version 19.14.26428.1 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

Compiler Passes:
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\cl.exe:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1xx.dll:      Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c2.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\link.exe:      Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\mspdb140.dll:  Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\1033\clui.dll: Version 19.14.26428.1

cl : Command line error D8003 : missing source filename
```

出力全体をコピーして、レポートに貼り付けます。

### <a name="the-command-line"></a>コマンド ライン

コードをビルドするために使われた正確なコマンド ライン、cl.exe、およびそのすべての引数が必要です。 そうであれば、弊社のコンピューターでまったく同じ方法によりビルドできます。 それは、特定の引数または引数の組み合わせを使ってビルドしたときにのみ問題が発生する可能性があるので重要です。

この情報を検索する最適な場所は、問題が発生した直後のビルド ログです。 そのようにすると、問題の原因となった可能性があるまったく同じ引数がコマンド ラインに確実に含まれます。

#### <a name="to-report-the-contents-of-the-command-line"></a>コマンド ラインの内容を報告するには

1. **CL.command.1.tlog** ファイルを探して開きます。 既定では、このファイルは、\\Visual Studio *version*\\Projects\\*SolutionName*\\*ProjectName*\\*Configuration*\\*ProjectName*.tlog\\CL.command.1.tlog 内のドキュメント フォルダー内、または \\Source\\Repos\\*SolutionName*\\*ProjectName*\\*Configuration*\\*ProjectName*.tlog\\CL.command.1.tlog の下のご自分のユーザー フォルダー内にあります。 別のビルド システムを使用している場合、またはプロジェクトの既定の場所を変更した場合は、別の場所にある可能性があります。

   このファイルで、ソース コード ファイルの名前と、コンパイルに使われたコマンド ライン引数を探します。これらは別々の行になっています。

1. 問題が発生するソース コード ファイルの名前を含む行を探します。 その下の行には、対応する cl.exe コマンド引数が含まれています。

コマンド ライン全体をコピーして、レポートに貼り付けます。

### <a name="a-description-of-the-problem"></a>問題の説明

問題の詳細な説明が必要です。 それにより、弊社のコンピューターで同じ結果を見ていることを確認できます。 また、実行しようとしていたこと、および予想された結果をお知らせいただくと、役に立つ場合があります。

ツールセットで表示される**正確なエラー メッセージ**、または発生した正確な実行時の動作を提供するのが、よい説明です。 この情報は、問題が正しく再現されたことを Microsoft が確認するために必要です。 最後のエラー メッセージだけでなく、**すべて**のコンパイラ出力を含めます。 Microsoft では、報告する問題が発生するまでのすべてのことを確認する必要があります。 コマンド ライン コンパイラを使用して問題を複製できる場合は、そのコンパイラの出力が推奨されます。 IDE およびその他のビルド システムは、表示されるエラー メッセージがフィルター処理されたり、エラー メッセージの最初の行のみがキャプチャされたりする場合があります。

コンパイラが無効なコードを受け入れ、診断を生成しないことが問題の場合、そのことをレポートに記載します。

実行時の動作の問題を報告するには、プログラムで出力されたものの**正確なコピー**と、表示されるべきものを含めます。 たとえば `printf("This should be 5: %d\n", actual_result);` のように、これが出力ステートメントそのものに含まれているのが理想的です。 プログラムがクラッシュまたはハングする場合は、そのことも記載してください。

発生した問題の診断に役立つ可能性があるその他の詳細 (自分で見つけた回避策など) を追加します。 レポートの別の場所にある情報を繰り返し記載しないようにしてください。

### <a name="the-repro"></a>再現コード

"*再現コード*" は、完全な自己完結型のソース コードの例です。 再現可能な方法で発生している問題を示します (これが名前の由来です)。 再現コードは、Microsoft のコンピューターでエラーを再現できるようにするために必要です。 コードは、それだけでコンパイルして実行する基本的な実行可能ファイルを作成するのに十分である必要があります。 または、見つかった問題がなければ、コンパイルして実行 "*できたはずのもの*" です。 再現コードはコード スニペットではありません。 完全な関数とクラスがあり、標準のヘッダーに対しても、必要なすべての #include ディレクティブが含まれている必要があります。

#### <a name="what-makes-a-good-repro"></a>適切な再現コードを作成には

適切な再現コード:

- **最小限である**。 再現コードは、発生した問題を正確に再現しながら、可能な限り小さくする必要があります。 再現コードは複雑または現実的なものである必要はありません。 必要なのは、標準または文書化されているコンパイラの実装に準拠しているコードを示すことだけです。 診断が存在しない場合は、再現コードで適合しないコードを示す必要があります。 問題を再現するのに十分なコードを含むシンプルで的を射た再現コードが最適です。 準拠した状態を保ち、さらに問題を変更せずに、コードを除去または簡素化できる場合は、そのようにします。 動作するコードの反例を含める必要はありません。

- **自己完結的である**。 再現手順には、必要のない依存関係を含めないようにする必要があります。 サード パーティ製のライブラリがなくても問題を再現できる場合は、使わずに再現します。 単純な出力ステートメントだけでなく、ライブラリ コードがなくても、問題を再現できる場合は (たとえば、`puts("this shouldn't compile");`、`std::cout << value;`、`printf("%d\n", value);`)、そのようにします。 これは、ユーザー ヘッダーへの参照なしで例を 1 つのソース コード ファイルに凝縮できる場合に最適です。 問題の可能性のある原因として考える必要のあるコードの量を減らすことは、調査するときにとても役に立ちます。

- **最新バージョンのコンパイラが対象である**。 再現コードでは、可能な場合には常に、最新バージョンのツールセットの最新の更新プログラムを使用する必要があります。 または、次回の更新プログラムまたは次のメジャー リリースの最新のプレリリース版を使用します。 古いバージョンのツールセットで発生する問題の多くは、新しいバージョンで修正されています。 修正プログラムが以前のバージョンに移植されるのは、例外的な状況でだけです。

- **他のコンパイラで確認されている** (関連する場合)。 移植可能な C++ コードに関係のある再現手順は、可能であれば、他のコンパイラで動作を確認する必要があります。 C++ 標準では、プログラムの正確性が最終的に判断され、完全なコンパイラはありません。 ただし、Clang と GCC が診断なしでコードを受け入れ、MSVC が受け入れない場合は、お使いのコンパイラのバグが見つかった可能性があります。 (その他の可能性として、UNIX と Windows の動作の違いや、C++ の標準実装のレベルの違いなどがあります)。すべてのコンパイラでコードが拒否される場合は、コードが間違っている可能性があります。 さまざまなエラー メッセージを見ることで、自分で問題を診断できる場合があります。

   コードをテストするオンライン コンパイラのリストは、ISO C++ Web サイトの[オンライン C++ コンパイラ](https://isocpp.org/blog/2013/01/online-c-compilers)、または GitHub の選別された[オンライン C++ コンパイラのリスト](https://arnemertz.github.io/online-compilers/)で見つけることができます。 具体的な例には、[Wandbox](https://wandbox.org/)、[Compiler Explorer](https://godbolt.org/)、[Coliru](https://coliru.stacked-crooked.com/) などがあります。

   > [!NOTE]
   > オンライン コンパイラの Web サイトは Microsoft とは関係ありません。 オンライン コンパイラの Web サイトの多くは、個人のプロジェクトとして運営されています。 これを読んでいる時点で閲覧できなくなっているサイトもあるかもしれませんが、検索すれば、その他の使用できるサイトが見つかるはずです。

コンパイラ、リンカー、ライブラリの問題は、特定の方法で発生する傾向があります。 発生した問題の種類により、レポートに含める必要がある再現コードの種類が決まります。 適切な再現コードがないと、調査するものがありません。 発生する可能性のあるいくつかの問題の種類を次に示します。 問題の種類ごとにレポートに使用する必要のある再現コードの種類の生成方法の手順も示します。

#### <a name="frontend-parser-crash"></a>フロントエンド (パーサー) のクラッシュ

フロントエンドのクラッシュは、コンパイラの解析フェーズの間に発生します。 通常、コンパイラでは、[致命的なエラー C1001](../error-messages/compiler-errors-1/fatal-error-c1001.md) が出力され、エラーが発生したソース コード ファイルと行番号が参照されます。 msc1.cpp という名前のファイルが言及されていることがよくありますが、この詳細は無視してかまいません。

この種のクラッシュの場合は、[前処理済み再現コード](#preprocessed-repros)を提供します。

この種のクラッシュに対するコンパイラ出力の例を次に示します。

```Output
SandBoxHost.cpp
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        fatal error C1001: An internal error has occurred in the compiler.
(compiler file 'msc1.cpp', line 1369)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        note: This diagnostic occurred in the compiler generated function
        'void Microsoft::Ceres::Common::Tools::Sandbox::SandBoxedProcess::Dispose(bool)'
Internal Compiler Error in d:\o\dev\otools\bin\x64\cl.exe.  You will be prompted
        to send an error report to Microsoft later.
INTERNAL COMPILER ERROR in 'd:\o\dev\otools\bin\x64\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

#### <a name="backend-code-generation-crash"></a>バックエンド (コード生成) のクラッシュ

バックエンドのクラッシュは、コンパイラのコード生成フェーズの間に発生します。 通常、コンパイラでは、[致命的なエラー C1001](../error-messages/compiler-errors-1/fatal-error-c1001.md) が出力され、問題に関連するソース コード ファイルと行番号が参照されていない場合があります。 ファイル compiler\\utc\\src\\p2\\main.c が言及されていることがよくありますが、この詳細は無視してかまいません。

この種のクラッシュの場合は、 **/GL** コマンド ライン引数を cl.exe に指定することによって有効したリンク時のコード生成 (LTCG) を使っている場合は、[リンク再現コード](#link-repros)を提供します。 使っていない場合は、代わりに[前処理済み再現コード](#preprocessed-repros)を提供します。

LTCG を使っていないバックエンド クラッシュに対するコンパイラ出力の例を次に示します。 次のようなコンパイラ出力の場合は、[前処理済み再現コード](#preprocessed-repros)を提供する必要があります。

```Output
repro.cpp
\\officefile\public\tadg\vc14\comperror\repro.cpp(13) : fatal error C1001:
        An internal error has occurred in the compiler.
(compiler file 'f:\dd\vctools\compiler\utc\src\p2\main.c', line 230)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
INTERNAL COMPILER ERROR in
        'C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\BIN\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

**内部コンパイラ エラー**で始まる行において、cl.exe ではなく link.exe が言及されている場合は、LTCG が有効になっていました。 この場合は、[リンク再現コード](#link-repros)を提供します。 コンパイラのエラー メッセージから LTCG が有効になっていたどうかはっきりわからない場合は、コマンド ライン引数を調べます。 それらは、前の手順で **/GL** コマンド ライン引数に対するビルド ログからコピーしました。

#### <a name="linker-crash"></a>リンカーのクラッシュ

リンカーのクラッシュは、コンパイラが実行された後のリンク フェーズ中に発生します。 通常、リンカーは[リンカー ツール エラー LNK1000](../error-messages/tool-errors/linker-tools-error-lnk1000.md) を出力します。

> [!NOTE]
> 出力が C1001 またはリンク時コード生成に関するものである場合は、「[バックエンド (コード生成) のクラッシュ](#backend-code-generation-crash)」をご覧ください。

この種のクラッシュの場合は、[リンク再現コード](#link-repros)を提供します。

この種のクラッシュに対するコンパイラ出力の例を次に示します。

```Output
z:\foo.obj : error LNK1000: Internal error during IMAGE::Pass2

  Version 14.00.22816.0

  ExceptionCode            = C0000005
  ExceptionFlags           = 00000000
  ExceptionAddress         = 00007FF73C9ED0E6 (00007FF73C9E0000)
        "z:\tools\bin\x64\link.exe"
  NumberParameters         = 00000002
  ExceptionInformation[ 0] = 0000000000000000
  ExceptionInformation[ 1] = FFFFFFFFFFFFFFFF

CONTEXT:

  Rax    = 0000000000000400  R8     = 0000000000000000
  Rbx    = 000000655DF82580  R9     = 00007FF840D2E490
  Rcx    = 005C006B006F006F  R10    = 000000655F97E690
  Rdx    = 000000655F97E270  R11    = 0000000000000400
  Rsp    = 000000655F97E248  R12    = 0000000000000000
  Rbp    = 000000655F97EFB0  E13    = 0000000000000000
  Rsi    = 000000655DF82580  R14    = 000000655F97F390
  Rdi    = 0000000000000000  R15    = 0000000000000000
  Rip    = 00007FF73C9ED0E6  EFlags = 0000000000010206
  SegCs  = 0000000000000033  SegDs  = 000000000000002B
  SegSs  = 000000000000002B  SegEs  = 000000000000002B
  SegFs  = 0000000000000053  SegGs  = 000000000000002B
  Dr0    = 0000000000000000  Dr3    = 0000000000000000
  Dr1    = 0000000000000000  Dr6    = 0000000000000000
  Dr2    = 0000000000000000  Dr7    = 0000000000000000
```

インクリメンタル リンクが有効になっていて、初期リンクが成功、つまり後続のインクリメンタル リンクの基になっている最初のフル リンクの後でのみクラッシュが発生する場合は、初期リンクが完了した後で変更されたソース ファイルに対応するオブジェクト (.obj) ファイルとライブラリ (.lib) ファイルのコピーも提供します。

#### <a name="bad-code-generation"></a>不正なコードの生成

不正なコードが生成されることはまれです。 コンパイラが誤って不適切なコードを生成し、アプリケーションが実行時にクラッシュすると発生します。 代わりに、正しいコードを生成するか、またはコンパイル時に問題を検出する必要があります。 発生している問題が不正なコードの生成の結果であると考えられる場合は、[バックエンド (コード生成) のクラッシュ](#backend-code-generation-crash)と同じようにレポートを処理してください。

この種のクラッシュでは、cl.exe に対して **/GL** コマンド ライン引数を使っている場合は、[リンク再現コード](#link-repros)を提供します。 使っていない場合は、[前処理済み再現コード](#preprocessed-repros)を提供します。

## <a name="how-to-generate-a-repro"></a>再現コードの生成方法

Microsoft での問題の原因究明には、[適切な再現コード](#what-makes-a-good-repro)が非常に重要です。 特定の種類の再現コードについて、以下で説明する手順を実行する前に、問題を示すコードをできる限り凝縮してください。 依存関係、必須のヘッダー、ライブラリの除去または最小化を試みます。 可能な場合は、使用するコンパイラ オプションとプリプロセッサ定義を制限します。

異なる種類の問題の報告に使うさまざまな種類の再現コードを生成する手順を次に示します。

### <a name="preprocessed-repros"></a>前処理済み再現コード

*前処理済みの再現コード*は、問題を示す単一のソース ファイルです。 C プリプロセッサの出力から生成されます。 作成するには、元の再現コードのソース ファイルで **/P** コンパイラ オプションを使用します。 このオプションでは、インクルードされているヘッダーがインライン化されて、他のソース ファイルとヘッダー ファイルへの依存関係が削除されます。 ローカル環境に依存する可能性のあるマクロ、#ifdef 条件、他のプリプロセッサ コマンドも解決されます。

> [!NOTE]
> 問題の原因が標準ライブラリの実装におけるバグの可能性がある場合、通常、問題が解決済みかどうかを確認するために最新の作業中の実装に置き換えるので、前処理済みの再現コードはあまり役に立ちません。 この場合は、再現コードを前処理しないでください。また、問題を 1 つのソース ファイルに減らすことができない場合は、コードを .zip ファイルなどにパッケージ化するか、IDE プロジェクトの再現コードの使用を検討してください。 詳細については、「[その他の再現コード](#other-repros)」を参照してください。

#### <a name="to-preprocess-a-source-code-file"></a>ソース コード ファイルを前処理するには

1. 「[コマンド ラインの内容を報告するには](#to-report-the-contents-of-the-command-line)」の説明に従って、再現コードをビルドするために使用したコマンド ライン引数をキャプチャします。

1. プロジェクトをビルドするために使用した Visual Studio のバージョンと構成アーキテクチャに一致する**開発者コマンド プロンプト**を開きます。

1. 再現コード プロジェクトを含むディレクトリに移動します。

1. 開発者コマンド プロンプト コンソール ウィンドウで、コマンド「**cl /P** *arguments* *filename.cpp*」を入力します。 *arguments* には、上でキャプチャした引数のリストを使用します。 *filename.cpp* は再現コードのソース ファイルの名前です。 このコマンドは、再現コードに使用したコマンド ラインをレプリケートしますが、プリプロセッサ パスの後、コンパイルを停止します。 その後、前処理済みのソース コードを *filename.i* に出力します。

C++/CX ソース コード ファイルを前処理している場合、または C++ モジュール機能を使用している場合は、いくつか追加の手順が必要です。 詳細については、以下のセクションを参照してください。

前処理済みのファイルを生成した後、その前処理済みファイルをコンパイルして問題が引き続き再現されることを確認してください。

#### <a name="to-confirm-the-preprocessed-file-still-repros-the-error"></a>前処理済みファイルでエラーが再現することを確認するには

1. 開発者コマンド プロンプト コンソール ウィンドウで、コマンド「**cl** *arguments* **/TP** *filename.i*」を入力して、cl.exe に前処理済みのファイルを C++ ソース ファイルとしてコンパイルするように指示します。 *arguments* は上でキャプチャしたものと同じ引数ですが、 **/D** 引数と **/I** 引数は、削除されています。 それらは前処理済みのファイルに既に含まれているためです。 *filename.i* は、前処理済みファイルの名前です。

1. 問題が再現することを確認します。

最後に、前処理済みの再現コード *filename*.i を自分のレポートに添付します。

### <a name="preprocessed-ccx-winrtuwp-code-repros"></a>前処理済みの C++/CX WinRT/UWP コードの再現

C++/CX を使用して実行可能ファイルをビルドしている場合は、前処理済みの再現コードを作成して検証するには、いくつか追加の手順が必要です。

#### <a name="to-preprocess-ccx-source-code"></a>C++/CX ソース コードを前処理するには

1. 「[ソース コード ファイルを前処理するには](#to-preprocess-a-source-code-file)」の手順に従って、前処理済みのソース ファイルを作成します。

1. 生成された _filename_.i ファイルを検索して **#using** ディレクティブを見つけます。

1. すべての参照先ファイルの一覧を作成します。 Windows\*.winmd ファイル、platform.winmd ファイル、および mscorlib.dll はすべて除外します。

前処理済みのファイルでまだ問題が再現することを検証するための準備

1. 前処理済みファイル用の新しいディレクトリを作成し、それを新しいディレクトリにコピーします。

1. **#using** リストから .winmd ファイルを新しいディレクトリにコピーします。

1. 新しいディレクトリに空の vccorlib.h ファイルを作成します。

1. 前処理済みファイルを編集して、mscorlib.dll の任意の **#using** ディレクティブを削除します。

1. 前処理済みファイルを編集して、任意の絶対パスをコピーした .winmd ファイルのベア ファイル名だけに変更します。

前処理済みのファイルで、上記のように、まだ問題が再現することを確認します。

### <a name="preprocessed-c-modules-repros"></a>前処理済み C++ モジュールの再現

C++ コンパイラのモジュール機能を使用している場合は、前処理済みの再現を作成して検証するには、いくつか異なる手順が必要です。

#### <a name="to-preprocess-a-source-code-file-that-uses-a-module"></a>モジュールを使用するソース コード ファイルを前処理するには

1. 「[コマンド ラインの内容を報告するには](#to-report-the-contents-of-the-command-line)」の説明に従って、再現コードをビルドするために使用したコマンド ライン引数をキャプチャします。

1. プロジェクトをビルドするために使用した Visual Studio のバージョンと構成アーキテクチャに一致する**開発者コマンド プロンプト**を開きます。

1. 再現コード プロジェクトを含むディレクトリに移動します。

1. 開発者コマンド プロンプト コンソール ウィンドウで、コマンド「**cl /P** *arguments* *filename.cpp*」を入力します。 *arguments* は上でキャプチャした引数、*filename.cpp* はモジュールを使用するソース ファイルの名前です。

1. モジュール インターフェイス (.ifc 出力) をビルドする再現プロジェクトを格納するディレクトリに変更します。

1. モジュール インターフェイスをビルドするために使用するコマンド ライン引数をキャプチャします。

1. 開発者コマンド プロンプト コンソール ウィンドウで、コマンド「**cl /P** *arguments* *modulename.ixx*」を入力します。 *arguments* は上でキャプチャした引数、*modulename.ixx* はモジュールのインターフェイスを作成するファイルの名前です。

前処理済みのファイルを生成した後、その前処理済みファイルを使用して問題が引き続き再現されることを確認してください。

#### <a name="to-confirm-the-preprocessed-file-still-repros-the-error"></a>前処理済みファイルでエラーが再現することを確認するには

1. 開発者コンソール ウィンドウで、自分の再現コード プロジェクトが含まれているディレクトリに戻ります。

1. 上記のように、コマンド **cl** *arguments* **/TP** *filename*.i を入力して、前処理済みファイルを C++ ソース ファイルの場合と同様にコンパイルします。

1. 前処理済みのファイルでまだ問題が再現することを確認します。

最後に、前処理済みの再現ファイル (*filename*.i と *modulename*.i) を .ifc 出力と共に、レポートに添付します。

### <a name="link-repros"></a>リンク再現コード

*リンク再現コード*は、**link\_repro** 環境変数で指定されたか、または [/LINKREPRO](../build/reference/linkrepro.md) リンカー オプションの引数として指定された、リンカーによって生成されたディレクトリ内容です。 これには、リンク時に発生する問題を全体として再現するビルド成果物が含まれます。 たとえば、リンク時コード生成 (LTCG) が関係するバックエンド クラッシュやリンカー クラッシュなどです。 これらのビルド成果物は、問題が再現できるように、リンカー入力として必要なものです。 リンク再現コードは、この環境変数を使用して、簡単に作成できます。 リンカーの組み込みの再現コード生成機能を有効にします。

#### <a name="to-generate-a-link-repro-using-the-link_repro-environment-variable"></a>link_repro 環境変数を使用してリンク再現コードを生成するには

1. 「[コマンド ラインの内容を報告するには](#to-report-the-contents-of-the-command-line)」の説明に従って、再現コードをビルドするために使用したコマンド ライン引数をキャプチャします。

1. プロジェクトをビルドするために使用した Visual Studio のバージョンと構成アーキテクチャに一致する**開発者コマンド プロンプト**を開きます。

1. 開発者コマンド プロンプト コンソール ウィンドウで、自分の再現コード プロジェクトが含まれているディレクトリに移動します。

1. **mkdir linkrepro** を入力して、リンク再現コードに対して *linkrepro* というディレクトリを作成します。 別のリンク再現コードをキャプチャするには、別の名前を使用します。

1. コマンド「**set link\_repro=linkrepro**」を入力して、作成したディレクトリに **link\_repro** 環境変数を設定します。 複雑なプロジェクトでよくあるように、別のディレクトリからビルドを実行する場合は、代わりに **link\_repro** をリンク再現コード ディレクトリへの完全なパスに設定します。

1. Visual Studio で再現コード プロジェクトをビルドするには、開発者コマンド プロンプト コンソール ウィンドウで、コマンド **devenv** を入力します。 これにより、**link\_repro** 環境変数の値を Visual Studio で認識できるようになります。 コマンド ラインでプロジェクトをビルドするには、上でキャプチャしたコマンド ライン引数を使用して再現コード ビルドを複製します。

1. 再現コード プロジェクトをビルドし、予想された問題が発生することを確認します。

1. Visual Studio を閉じます (ビルドを行うために使用した場合)。

1. 開発者コマンド プロンプト コンソール ウィンドウで、コマンド **set link\_repro=** を入力して、**link\_repro** 環境変数をクリアします。

最後に、linkrepro ディレクトリ全体を .zip ファイルなどに圧縮することで再現コードをパッケージ化し、レポートに添付します。

**/LINKREPRO** リンカーオプションには、**link\_repro** 環境変数と同じ効果があります。 生成されたリンク再現コードのフィルター処理に使用する名前を指定するには、[/LINKREPROTARGET](../build/reference/linkreprotarget.md) オプションを使用します。 **/LINKREPROTARGET** を使用するには、 **/OUT** リンカー オプションも指定する必要があります。

#### <a name="to-generate-a-link-repro-using-the-linkrepro-option"></a>/LINKREPRO オプションを使用してリンク再現コードを生成するには

1. リンク再現コードを保持するためのディレクトリを作成します。 ここでは、作成する完全なディレクトリ パスを _directory-path_ とします。 パスにスペースが含まれている場合は、パスを二重引用符で囲みます。

1. リンカー コマンド ラインに **/LINKREPRO:** _directory-path_ コマンドを追加します。 Visual Studio で、プロジェクトの **[プロパティ ページ]** ダイアログを開きます。 **[構成プロパティ]**  >  **[リンカー]**  >  **[コマンド ライン]** プロパティ ページを選択します。 次に、 **[追加オプション]** ボックスに「 **/LINKREPRO:** _directory-path_」オプションを入力します。 **[OK]** を選択して変更を保存します。

1. 再現コード プロジェクトをビルドし、予想された問題が発生することを確認します。

最後に、_directory-path_ リンク再現コード ディレクトリ全体を .zip ファイルなどに圧縮することで再現コードをパッケージ化し、レポートに添付します。

### <a name="other-repros"></a>その他の再現コード

1 つのソース ファイルまたは前処理済み再現コードに問題をまとめることができず、問題にリンク再現コードが必要ない場合は、IDE プロジェクトを調査できます。 適切な再現コードの作成方法に関するすべてのガイダンスが適用されます。コードは最小限の自己完結型にする必要があります。 問題は Microsoft の最新ツールで発生する必要があり、関連する場合は、他のコンパイラでは確認されない必要があります。

最小限の IDE プロジェクトとして再現コードを作成し、ディレクトリ構造全体を .zip ファイルなどに圧縮してパッケージ化した後、レポートに添付します。

## <a name="ways-to-send-your-report"></a>レポートを送信する方法

レポートを提出するのに最適な方法は、2 通りあります。 Visual Studio に組み込まれている[問題の報告ツール](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)、または [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) (Visual Studio 開発者コミュニティ) ページを使用できます。 また、このページの下部には **[製品のフィードバック]** ボタンがあります。 どちらを選択するかは、IDE の組み込みツールを使ってスクリーンショットをキャプチャし、レポートを整理するかどうかに依存します。 そうしたくない場合は、開発者コミュニティの Web サイトを直接使用できます。

> [!NOTE]
> レポートの送信方法に関係なく、Microsoft はお客様のプライバシーを尊重します。 Microsoft は、すべてのデータのプライバシーに関する法律および規制を遵守することに努めています。 お客様から送信していただいたデータの扱いについて詳しくは、「[Microsoft のプライバシーに関する声明](https://privacy.microsoft.com/privacystatement)」をご覧ください。

### <a name="use-the-report-a-problem-tool"></a>問題の報告ツールを使う

Visual Studio の**問題の報告**ツールを使うと、Visual Studio のユーザーはわずか数クリックで問題を報告できます。 ポップアップ表示される簡単なフォームで、見つかった問題に関する詳細情報を送信します。 IDE を終了することなく、レポートを送信できます。

**問題の報告**ツールを通して問題を報告する方法は、IDE からは簡単で便利です。 このツールには、 **[サイド リンク バー]** 検索ボックスの横にある **[フィードバックの送信]** アイコンを選択することにより、タイトル バーからアクセスすることができます。 または、メニュー バーから、 **[ヘルプ]**  >  **[フィードバックの送信]**  >  **[問題の報告]** の順に選択してアクセスすることもできます。

問題を報告することにした場合は、まず、開発者コミュニティを調べて同様の問題が発生していないかを確認します。 以前に同様の問題が報告されている場合は、そのレポートに賛成票を投じ、具体例な説明を含めたコメントを追加します。 同様の問題が見つからない場合は、Visual Studio フィードバック ダイアログの下部にある **[新しい問題を報告する]** ボタンを選択して、問題を報告するための手順に従います。

### <a name="use-the-visual-studio-developer-community-pages"></a>Visual Studio 開発者コミュニティ ページを使用する

Visual Studio で問題を報告するためのもう 1 つの便利な方法として Visual Studio 開発者コミュニティ ページがあります。このページでは Visual Studio および C++ コンパイラ、ツール、ライブラリについて解決策を検索できます。 [Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html)、[Visual Studio for Mac](https://developercommunity.visualstudio.com/spaces/41/index.html)、[.NET](https://developercommunity.visualstudio.com/spaces/61/index.html)、[C++](https://developercommunity.visualstudio.com/spaces/62/index.html)、[Azure DevOps Services](https://developercommunity.visualstudio.com/spaces/21/index.html)、および [TFS](https://developercommunity.visualstudio.com/spaces/22/index.html) の特定の開発者コミュニティ ページがあります。

コミュニティのタブの下にある各ページの上部付近には、検索ボックスがあります。 自分と似た問題を報告している投稿を検索するために使用できます。 遭遇している問題に関連する解決策またはその他の有用な情報が既に報告されていることがあります。 他のユーザーが以前に同じ問題を報告している場合は、新たに問題レポートを作成するのではなく、そのレポートに対して賛成票を投じ、コメントを追加します。 新しい問題についてコメント、投票、または報告するには、Visual Studio アカウントへのサインインを求められる場合があります。 初めてサインインするときは、開発者コミュニティ アプリがプロファイルにアクセスすることに同意する必要があります。

C++ コンパイラ、リンカー、およびその他のツールやライブラリでの問題については、[C++](https://developercommunity.visualstudio.com/spaces/62/index.html) に関するページを使用してください。 問題を検索し、以前にその問題が報告されていない場合は、検索ボックスの横にある **[問題の報告]** ボタンを選択します。 再現コードとコマンド ライン、スクリーンショット、関連するディスカッションへのリンク、および関連性があり有用だと思われるその他の情報を含めることができます。

> [!TIP]
> Visual Studio で発生する可能性がある、C++ ツールセットに関係しない他の種類の問題 (たとえば、UI の問題、IDE の機能の不具合、一般的なクラッシュなど) の場合は、IDE の**問題の報告**ツールを使用します。 スクリーンショット機能や、発生した問題の原因である UI 操作を記録する機能があるので、このツールは最適です。 このようなエラーについても、[開発者コミュニティ](https://developercommunity.visualstudio.com/) サイトで検索できます。 詳細については、「[Visual Studio で問題を報告する方法](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)」を参照してください。

### <a name="reports-and-privacy"></a>レポートとプライバシー

**既定では、レポート内のすべての情報、およびコメントと応答はすべて公開されます**。 通常それには、コミュニティ全体が問題、解決策、および他のユーザーが見つけた回避策を閲覧できるという利点があります。 しかし、プライバシーや知的財産権の理由から、データや ID が公開されることを心配されている場合は、いくつかオプションがあります。

身元を公開することについて心配がある場合は、個人情報を公開しない[新しい Microsoft アカウントを作成](https://signup.live.com/)します。 このアカウントを使用してレポートを作成します。

**公開される最初のレポートのタイトルや内容に、公開したくないことを含めないでください。** 代わりに、別のコメントで詳細を非公開で送信することができます。 レポートが適切な担当者に確実に送信されるようにするためには、問題レポートのトピックの一覧に **cppcompiler** を含めます。 問題レポートが作成されると、返信と添付ファイルを閲覧できる人を指定することができるようになります。

#### <a name="to-create-a-problem-report-for-private-information"></a>個人情報の問題レポートを作成するには

1. 作成したレポートで、 **[コメントの追加]** を選択して、問題の個人的な詳細を作成します。

1. 返信エディターで、 **[送信]** ボタンと **[キャンセル]** ボタンの下のドロップダウン コントロールを使用して、返信を閲覧できる人を指定します。 指定された人だけがこれらの非公開の返信と、それに含まれるイメージ、リンク、またはコードを閲覧できます。 閲覧できるのを Microsoft の従業員と自分に制限するには、 **[Viewable by moderators and the original poster]\(モデレーターと元の投稿者が閲覧可能\)** を選択します。

1. 説明と、問題の再現に必要なその他の情報、イメージ、および、添付ファイルを追加します。 **[送信]** ボタンを選択して、非公開でこの情報を送信します。

   添付ファイルには 2 GB の制限があり、最大で 10 個のファイルに制限されています。 これを超えるアップロードについては、プライベート コメントでアップロード URL を要求します。

このコメントの下のすべての返信には、指定したのと同じ閲覧制限が適用されます。 それは、応答のドロップダウン コントロールに閲覧制限の状態が正しく表示されていない場合でも当てはまります。

お客様のプライバシーと機密情報が公開されないようにするため、注意してください。 Microsoft とのすべてのやり取りは、制限付きのコメントの下で返信するようにしてください。 他のコメントに返信すると、機密情報が誤って公開される場合があります。

## <a name="how-to-report-a-c-documentation-issue"></a>C++ ドキュメントの問題を報告する方法

Microsoft では、GitHub の問題を使用して、報告されているドキュメントの問題を追跡しています。 現在 GitHub の問題は、コンテンツ ページから直接作成できます。これでは、ライターや製品チームとさまざまな方法で問題に関して直接やり取りできます。 ドキュメントに問題がある場合、コード サンプルが不適切な場合、説明が不明瞭な場合、重要な欠落がある場合、または単に記述間違いがある場合、簡単にご連絡いただけます。 ページの一番下までスクロールし、 **[Sign in to give documentation feedback]** \(サインインしてドキュメントのフィードバックを送信する\) を選択します。 まだお持ちでない場合は、GitHub アカウントを作成する必要があります。 GitHub アカウントを作成すれば、すべてのドキュメントに関する問題やそれらの状態を参照できます。 また、お客様から報告された問題が変更された場合、通知を受け取ることができます。 詳細については、「[A New Feedback System Is Coming to docs.microsoft.com](/teamblog/a-new-feedback-system-is-coming-to-docs)」(docs.microsoft.com に導入される新しいフィードバック システム) を参照してください。

ドキュメントのフィードバック ボタンを使用して、ドキュメントの問題を GitHub で作成します。 問題を作成したページに関するいくつかの情報が、問題に自動的に記入されます。 それによって、問題がどこにあるかが Microsoft に把握されるので、この情報は編集しないでください。 問題の箇所の詳細のみを添付し、必要に応じて、修正方法の提案をお知らせください。 [当社の C++ ドキュメントはオープンソース](https://github.com/MicrosoftDocs/cpp-docs/)なので、自分で修正を送信したい場合はそれを行えます。 弊社のドキュメントにご協力いただく方法の詳細については、GitHub の「[Contributing guide](https://github.com/MicrosoftDocs/cpp-docs/blob/master/CONTRIBUTING.md)」 (寄稿ガイド) を参照してください。
