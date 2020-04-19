---
title: /clr の制約
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
ms.openlocfilehash: d0318ce2e23f92600d5a78d6472646ec91492152
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837375"
---
# <a name="clr-restrictions"></a>/clr の制約

**/clr** の使用に関する次の制限事項に注意してください。

- 構造化例外ハンドラーでは、 **/clr** でコンパイルする際の `_alloca` の使用に関する制限事項があります。 詳細については、「[_alloca](../../c-runtime-library/reference/alloca.md)」を参照してください。

- **/clr** では実行時エラー チェックは使用できません。 詳細については、「[方法 :ネイティブ ランタイム チェックを使用する](/visualstudio/debugger/how-to-use-native-run-time-checks)」を参照してください。

- **/clr** を使用して、標準の C++ 構文のみを使用するプログラムをコンパイルする場合は、インライン アセンブリの使用に次のガイドラインが適用されます。

  - ネイティブ スタック レイアウト、現在の関数の外部の呼び出し規則、またはコンピューターに関するその他の低レベルの情報に関する知識を想定しているインライン アセンブリ コードは、その知識がマネージド関数のスタック フレームに適用される場合、エラーになる可能性があります。 インライン アセンブラー コードを含む関数は、 **/clr** なしでコンパイルされた別個のモジュール内に配置された場合と同様に、アンマネージド関数として生成されます。

  - コピーで構築された関数のパラメーターを渡す関数内のインライン アセンブリ コードはサポートされていません。

- **/clr** でコンパイルされたプログラムから [Vprintf 系関数](../../c-runtime-library/vprintf-functions.md)を呼び出すことはできません。

- /clr では [naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) 修飾子は無視されます。

- [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) で設定された変換関数は、アンマネージド コード内のキャッチにのみ影響を与えます。 詳細については、「[例外処理](../../extensions/exception-handling-cpp-component-extensions.md)」を参照してください。

- **/clr** では、関数ポインターの比較は許可されません。

- **/clr** では、完全なプロトタイプ関数以外の関数は使用できません。

- **/clr** では、次のコンパイラ オプションはサポートされていません。

  - **/EHsc** と **/EHs** ( **/clr** は **/EHa** を意味します) (「[/EH (例外処理モデル)](eh-exception-handling-model.md)」を参照)

  - **/fp:strict** と **/fp:except** (「[/fp (浮動小数点の動作の指定)](fp-specify-floating-point-behavior.md)」を参照)

  - [/Zd](z7-zi-zi-debug-information-format.md)

  - [/Gm](gm-enable-minimal-rebuild.md)

  - [/MT](md-mt-ld-use-run-time-library.md)

  - [/RTC](rtc-run-time-error-checks.md)

  - [/ZI](z7-zi-zi-debug-information-format.md)

- `_STATIC_CPPLIB` プリプロセッサの定義 (`/D_STATIC_CPPLIB`) と **/clr** コンパイラ オプションの組み合わせはサポートされていません。 この定義により、アプリケーションが、サポートされていない静的なマルチスレッド C++ 標準ライブラリとリンクされるためです。 詳細については、「[/MD、/MT、/LD (ランタイム ライブラリの使用)](md-mt-ld-use-run-time-library.md)」のトピックを参照してください。

- **/clr** で **/Zi** を使用すると、パフォーマンスに影響を与えます。 詳細については、「[/Zi](z7-zi-zi-debug-information-format.md)」を参照してください。

- [/Zc:wchar_t](zc-wchar-t-wchar-t-is-native-type.md) を一緒に指定せずに、またはこの文字を `__wchar_t` にキャストせずに、ワイド文字を .NET Framework 出力ルーチンに渡すと、出力が`unsigned short int`として表示されます。 次に例を示します。

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- 関数が `#pragma` [unmanaged](../../preprocessor/managed-unmanaged.md) 下にない場合、または関数をネイティブにコンパイルする必要がある場合、 **/clr** でコンパイルすると [/GS](gs-buffer-security-check.md) は無視されます。この場合、コンパイラで警告 C4793 が生成され、これは既定ではオフになります。

- マネージド アプリケーションの関数シグネチャ要件については、「[/ENTRY](entry-entry-point-symbol.md)」を参照してください。

- **/openmp** と **/clr** でコンパイルされたアプリケーションは、1 つの AppDomain プロセスでのみ実行できます。  詳細については、「[/openmp (OpenMP 2.0 サポートの有効化)](openmp-enable-openmp-2-0-support.md)」を参照してください。

- 可変個引数 (vararg) を受け取る関数は、ネイティブ関数として生成されます。 可変個引数の位置にあるすべてのマネージド データ型は、ネイティブ型にマーシャリングされます。 <xref:System.String?displayProperty=fullName> 型は、実際にはワイド文字の文字列ですが、1 バイト文字の文字列にマーシャリングされます。 したがって、printf 指定子が %S (wchar_t*) である場合、代わりに %s 文字列にマーシャリングされます。

- va_arg マクロを使用する場合、 **/clr:pure** でコンパイルすると予期しない結果が生じる可能性があります。 詳細については、「[va_arg、va_copy、va_end、va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)」を参照してください。 **/clr:pure** および **/clr:safe** コンパイラ オプションは Visual Studio 2015 では非推奨とされており、Visual Studio 2017 以降ではサポートされていません。 "純粋" または "安全" でなければならないコードは C# に移植する必要があります。

- マネージド コードから、パラメーター情報 (関数の引数) を取得するためにスタックを調べる関数を呼び出さないでください。P/invoke レイヤーにより、その情報がスタック内のさらに下位に移動します。  たとえば、 **/clr** でプロキシ/スタブをコンパイルしないでください。

- 関数は、可能な限りマネージド コードにコンパイルされますが、すべての C++ コンストラクトをマネージド コードに変換できるわけではありません。  この判断は関数ごとに行われます。 関数のいずれかの部分をマネージド コードに変換できない場合は、代わりに関数全体がネイティブ コードに変換されます。 次の場合は、コンパイラでマネージド コードが生成されません。

  - コンパイラによって生成されたサンクまたはヘルパー関数。 仮想関数呼び出しなど、関数ポインターを介したすべての関数呼び出しで、ネイティブ サンクが生成されます。

  - `setjmp` または `longjmp` を呼び出す関数。

  - 特定の組み込みルーチンを使用して、マシン リソースを直接操作する関数。 たとえば、`__enable` と `__disable`、`_ReturnAddress` と `_AddressOfReturnAddress`、またはマルチメディアの組み込み関数を使用すると、すべてネイティブ コードになります。

  - `#pragma unmanaged` ディレクティブに続く関数  (なお、逆の `#pragma managed` もサポートされています)。

  - 配列型 (`__declspec(align(...))` を使用して宣言された型) への参照を含む関数。

## <a name="see-also"></a>関連項目

- [/clr (共通言語ランタイムのコンパイル)](clr-common-language-runtime-compilation.md)
