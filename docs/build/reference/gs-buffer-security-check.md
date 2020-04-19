---
title: /GS (バッファーのセキュリティ チェック)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BufferSecurityCheck
- VC.Project.VCCLCompilerTool.BufferSecurityCheck
- /GS
helpviewer_keywords:
- buffers [C++], buffer overruns
- buffer overruns, compiler /GS switch
- GS compiler option [C++]
- /GS compiler option [C++]
- security check compiler option [C++]
- -GS compiler option [C++]
- buffers [C++], avoiding overruns
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
ms.openlocfilehash: 10afa874092eb563903ba5f49c6add136afc869c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292173"
---
# <a name="gs-buffer-security-check"></a>/GS (バッファーのセキュリティ チェック)

関数のリターン アドレス、例外ハンドラーのアドレス、または特定の型のパラメーターを上書きするバッファー オーバーランを検出します。 ハッカーは、バッファー オーバーランを発生させるという方法を使用して、バッファー サイズ制限を強制しないコードを攻撃します。

## <a name="syntax"></a>構文

```
/GS[-]
```

## <a name="remarks"></a>Remarks

**/GS**が既定でオンです。 アプリケーションにセキュリティを損なうがない場合を使用して、 **/GS-** します。 バッファー オーバーランの検出を抑制する詳細については、次を参照してください。 [safebuffers](../../cpp/safebuffers.md)します。

## <a name="security-checks"></a>セキュリティ チェック

バッファー オーバーランの問題を起こしやすいとコンパイラが判断した関数には、スタックのリターン アドレスの前に記憶領域が割り当てられます。 関数のエントリを割り当てられた領域が読み込まれて、*セキュリティ クッキー*モジュールの読み込み時に 1 回計算するがします。 関数の実行の終了時に、および 64 ビット オペレーティング システムでのフレームのアンワインド時に、ヘルパー関数が呼び出されてクッキーの値が変更されていないかどうかが確認されます。 異なる値は、スタックの上書きが発生した可能性があることを示します。 異なる値が検出された場合、プロセスは終了します。

## <a name="gs-buffers"></a>GS バッファー

バッファー オーバーラン セキュリティ チェックが実行される、 *GS バッファー*します。 GS バッファーは、次のいずれかを使用できます。

- 4 バイトを超える配列で、3 つ以上の要素を持ち、要素型がポインター型ではない配列。

- サイズが 8 バイトを超え、ポインターを含まないデータ構造体。

- 使用して割り当てられたバッファー、 [_alloca](../../c-runtime-library/reference/alloca.md)関数。

- GS バッファーを含むクラスまたは構造体。

たとえば、次のステートメントで GS バッファーを宣言します。

```cpp
char buffer[20];
int buffer[20];
struct { int a; int b; int c; int d; } myStruct;
struct { int a; char buf[20]; };
```

ただし、次のステートメントでは GS バッファーは宣言されません。 最初の 2 つの宣言には、ポインター型の要素が含まれます。 3 番目と 4 番目のステートメントでは、サイズが非常に小さい配列を宣言しています。 5 番目のステートメントでは、x86 プラットフォームでサイズが 8 バイトを超えない構造体を宣言しています。

```cpp
char *pBuf[20];
void *pv[20];
char buf[4];
int buf[2];
struct { int a; int b; };
```

## <a name="initialize-the-security-cookie"></a>セキュリティ クッキーの初期化

**/GS**コンパイラ オプションは、cookie を使用する任意の関数の実行前に、セキュリティ クッキーが初期化されることが必要です。 セキュリティ クッキーは、EXE または DLL にエントリをすぐに初期化する必要があります。 既定の VCRuntime エントリ ポイントを使用する場合に自動的にこれは、: mainCRTStartup、wmainCRTStartup、WinMainCRTStartup、wWinMainCRTStartup、または _DllMainCRTStartup します。 呼び出して、セキュリティ クッキーを手動で初期化する必要があります、別のエントリ ポイントを使用する場合 [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md) です。

## <a name="what-is-protected"></a>保護される対象

**/GS**コンパイラ オプションは、次の項目を保護します。

- 関数呼び出しの戻りアドレス。

- 関数の例外ハンドラーのアドレス。

- Vulnerable 関数パラメーター。

すべてのプラットフォームで **/GS**リターン アドレスへのバッファー オーバーランの検出を試みます。 バッファー オーバーランは、関数呼び出しのリターン アドレスをスタックに格納する呼び出し規則を使用する、x86、x64 などのプラットフォームでの方が簡単に攻撃されます。

x86 で、関数が例外ハンドラーを使用する場合、コンパイラはセキュリティ クッキーを挿入して、例外ハンドラーのアドレスを保護します。 このクッキーは、フレームのアンワインド時にチェックされます。

**/GS**保護*脆弱なパラメーター*関数に渡すことです。 脆弱なパラメーターとは、ポインター、C++ 参照、内部にポインターを含む C 構造体 (C++ POD 型)、または GS バッファーです。

脆弱なパラメーターは、クッキーおよびローカル変数より前に割り当てられます。 バッファー オーバーランによって、これらのパラメーターが上書きされることがあります。 また、これらのパラメーターを使用する関数のコードでは、関数から制御が戻る前、およびセキュリティ チェックが実行される前に、攻撃を受ける可能性があります。 この危険を最小化するために、コンパイラは、関数プロローグで、脆弱なパラメーターのコピーを作成し、任意のバッファーのストレージ領域の下に配置します。

コンパイラは、次の場合は脆弱なパラメーターのコピーを作成しません。

- GS バッファーを含まない関数の場合。

- 最適化 ([/O オプション](o-options-optimize-code.md)) 有効ではありません。

- 可変個引数リスト (...) を持つ関数の場合。

- マークされている関数[naked](../../cpp/naked-cpp.md)します。

- 最初のステートメントにインライン アセンブラー コードを含む関数の場合。

- パラメーターが、バッファー オーバーランが発生したときに攻撃される可能性が低い方法でのみ使用されている場合。

## <a name="what-is-not-protected"></a>保護されない対象

**/GS**コンパイラ オプションはすべてのバッファー オーバーラン セキュリティ攻撃から保護されません。 たとえば、バッファーと vtable が同じオブジェクトにある場合、バッファー オーバーランによって vtable が破損する可能性があります。

使用する場合でも **/GS**、常にバッファー オーバーランがない、セキュリティで保護されたコードを記述してください。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>このコンパイラ オプションを Visual Studio で使用するには

1. **ソリューション エクスプ ローラー**プロジェクトを右クリックし、クリックして**プロパティ**します。

   詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **プロパティ ページ**ダイアログ ボックスで、をクリックして、 **C/C++** フォルダー。

1. をクリックして、**コード生成**プロパティ ページ。

1. 変更、**バッファー セキュリティ チェック**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>

## <a name="example"></a>例

この例では、バッファー オーバーランが発生します。 このため、実行時にアプリケーションで障害が発生します。

```C
// compile with: /c /W1
#include <cstring>
#include <stdlib.h>
#pragma warning(disable : 4996)   // for strcpy use

// Vulnerable function
void vulnerable(const char *str) {
   char buffer[10];
   strcpy(buffer, str); // overrun buffer !!!

   // use a secure CRT function to help prevent buffer overruns
   // truncate string to fit a 10 byte buffer
   // strncpy_s(buffer, _countof(buffer), str, _TRUNCATE);
}

int main() {
   // declare buffer that is bigger than expected
   char large_buffer[] = "This string is longer than 10 characters!!";
   vulnerable(large_buffer);
}
```

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
