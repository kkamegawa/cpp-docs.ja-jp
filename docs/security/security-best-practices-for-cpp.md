---
title: C++ のセキュリティ推奨事項
ms.date: 05/08/2018
f1_keywords:
- securitybestpracticesVC
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
ms.openlocfilehash: eaaa581ff622438c2e395c34b4b026aca693a845
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416161"
---
# <a name="security-best-practices-for-c"></a>C++ のセキュリティ推奨事項

ここでは、セキュリティ ツールおよびセキュリティ対策について説明します。 これらを使用しても、アプリケーションを攻撃から完全に防御できるわけではありませんが、攻撃が成功する可能性を低減できます。

## <a name="visual-c-security-features"></a>Visual C++ セキュリティ機能

これらのセキュリティ機能は、Microsoft C++コンパイラとリンカーに組み込まれています。

[/guard (制御フロー ガードを有効にする)](../build/reference/guard-enable-control-flow-guard.md)<br/>
コンパイラは、コンパイル時に間接呼び出しターゲットの制御フローを分析し、実行時にターゲットを確認するコードを挿入します。

[/GS (バッファーのセキュリティ チェック)](../build/reference/gs-buffer-security-check.md)<br/>
利用される危険性がある関数に、オーバーラン検出コードがコンパイラによって挿入されます。 オーバーランが検出されると、実行が停止します。 このオプションの既定値はオンです。

[/SAFESEH (安全な例外ハンドラーがあるイメージ)](../build/reference/safeseh-image-has-safe-exception-handlers.md)<br/>
各例外ハンドラーのアドレスを格納したテーブルが、リンカーによって出力イメージに含められます。 実行時に、オペレーティング システムはこのテーブルを使用して適切な例外ハンドラーのみが実行されるようにします。 これにより、実行時に悪意のある攻撃を受けて例外ハンドラーが実行されることを回避できます。 このオプションの既定値はオフです。

[/NXCOMPAT](../build/reference/nxcompat.md)、 [/NXCOMPAT (データ実行防止と互換性あり)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md) 。これらのコンパイラオプションとリンカーオプションでは、データ実行防止 (DEP) の互換性が有効になります。 DEP は、CPU で非コード ページが実行されないようにします。

[/analyze (コード分析)](../build/reference/analyze-code-analysis.md)<br/>
このコンパイラ オプションを使用すると、潜在的なセキュリティ上の問題 (バッファー オーバーラン、非初期化メモリ、null ポインターの逆参照、メモリ リークなど) を報告するコード解析がアクティブになります。 このオプションの既定値はオフです。 詳細については、「[コード分析のC++ C/概要](/cpp/code-quality/code-analysis-for-c-cpp-overview)」を参照してください。

[/DYNAMICBASE (ASLR (Address Space Layout Randomization) の使用)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)<br/>
このリンカー オプションにより、実行開始時にメモリ内の個別の場所で読み込むことができる実行可能イメージをビルドできます。 また、このオプションを使用すると、メモリ内のスタックの位置を予測することが非常に難しくなります。

## <a name="security-enhanced-crt"></a>セキュリティが拡張された CRT

C ランタイム ライブラリ (CRT) が強化され、セキュリティ上のリスクをもたらす関数 (チェックが適用されない文字列コピー関数 `strcpy` など) の安全なバージョンが導入されました。 このようなセキュリティが万全ではない以前の関数は非推奨とされるため、これらの関数を使用すると、コンパイル時に警告が表示されます。 コンパイル時に警告が表示されないようにするのではなく、これらの CRT 関数の安全なバージョンを使用することをお勧めします。 詳細については、「 [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md)」を参照してください。

## <a name="safeint-library"></a>SafeInt ライブラリ

[SafeInt ライブラリ](../safeint/safeint-library.md)は、アプリケーションが数学的な操作を実行したときに発生する可能性がある、整数オーバーフローやその他の悪用可能なエラーを回避するのに役立ちます。 `SafeInt` ライブラリには、 [Safeint クラス](../safeint/safeint-class.md)、 [safeintexception クラス](../safeint/safeintexception-class.md)、およびいくつかの[safeint 関数](../safeint/safeint-functions.md)が含まれています。

`SafeInt` クラスを使用することで、整数オーバーフローおよびゼロ除算による攻撃を防止できます。 型が異なる値の比較を処理するために使用できます。 2つのエラー処理ポリシーが用意されています。 `SafeInt` クラスの既定のポリシーは、`SafeIntException` クラス例外をスローして、数値演算を完了できない理由を報告することです。 `SafeInt` クラスの 2 番目のポリシーは、プログラムの実行を停止することです。 カスタム ポリシーも定義できます。

各 `SafeInt` 関数は、対応する 1 つの数値演算で、攻撃に利用される可能性のあるエラーが発生しないようにします。 種類の異なる 2 つのパラメーターを使用できます。これらを同じ型に変換する必要はありません。 複数の数値演算を保護するには、`SafeInt` クラスを使用します。

## <a name="checked-iterators"></a>チェックを行う反復子

チェックを行う反復子は、コンテナー境界を強制します。 既定では、チェックを行う反復子が境界の外側にあると、例外が生成され、プログラムの実行が終了します。 チェックを行う反復子は、プリプロセッサ定義に割り当てられた値に依存する他のレベルの応答を提供します。たとえば、 **\_のセキュリティで保護された\_SCL\_スロー**し、 **\_反復子\_デバッグ\_レベル**です。 たとえば、 **\_反復子\_デバッグ\_レベル = 2**の場合、チェックを行う反復子はデバッグモードでの包括的な正確性チェックを提供します。これは、アサートを使用して利用できます。 詳細については、「チェックを行う[反復子](../standard-library/checked-iterators.md)」および「 [\_反復子\_デバッグ\_レベル](../standard-library/iterator-debug-level.md)」を参照してください。

## <a name="code-analysis-for-managed-code"></a>マネージド コードのコード分析

マネージド コードのコード分析は FxCop とも呼ばれ、.NET Framework デザイン ガイドラインに準拠するためにアセンブリをチェックします。 FxCop は各アセンブリ内のコードとメタデータを解析して、次の点に不備がないかどうかを検証します。

- ライブラリ デザイン

- ローカリゼーション

- 名前付け規則

- パフォーマンス テスト

- セキュリティ

## <a name="windows-application-verifier"></a>Windows アプリケーション検証ツール

[アプリケーション検証ツール (AppVerifier)](/windows-hardware/drivers/debugger/enable-application-verifier)は、潜在的なアプリケーションの互換性、安定性、およびセキュリティの問題を特定するのに役立ちます。

AppVerifier は、アプリケーションがどのようにオペレーティング システムを使用するのかを監視します。 AppVerifier は、アプリケーションの実行中に、ファイル システム、レジストリ、メモリ、および API を監視し、AppVerifier がカバーしない問題については、ソース コードの修正を推奨します。

AppVerifier は、次の用途で使用できます。

- 一般的なプログラミング上の誤りが原因で発生する潜在的なアプリケーションの互換性エラーがないかどうかをテストします。

- アプリケーションにメモリ関連の問題がないかどうかを調べます。

- アプリケーションの潜在的なセキュリティ上の問題を特定します。

## <a name="windows-user-accounts"></a>Windows ユーザー アカウント

Administrators グループに属する Windows ユーザー アカウントを使用すると、開発者とユーザー (機能拡張により) がセキュリティ上の危険にさらされます。 詳細については、「 [Users グループのメンバーとしての実行](running-as-a-member-of-the-users-group.md)」および「[ユーザーアカウント制御 (UAC) によるアプリケーション](how-user-account-control-uac-affects-your-application.md)への影響」を参照してください。

## <a name="guidance-for-speculative-execution-side-channels"></a>予測実行側チャネルに関するガイダンス

ソフトウェアにおけるC++予測実行側チャネルハードウェアの脆弱性に対する識別と軽減方法の詳細については、「予測[ C++実行側チャネルの開発者ガイド](developer-guidance-speculative-execution.md)」を参照してください。

## <a name="see-also"></a>参照

<xref:System.Security> <br/>
[セキュリティ](/dotnet/standard/security/index)<br/>
[ユーザー アカウント制御 (UAC: User Account Control) がアプリケーションに与える影響](how-user-account-control-uac-affects-your-application.md)
