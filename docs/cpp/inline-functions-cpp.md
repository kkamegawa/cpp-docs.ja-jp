---
title: インライン関数 (C++)
ms.date: 10/09/2018
f1_keywords:
- __forceinline_cpp
- __inline_cpp
- inline_cpp
- __inline
- _inline
- __forceinline
- _forceinline
helpviewer_keywords:
- inline functions [C++], class members
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
ms.openlocfilehash: efaaacc46f63ac1a702ab2110d35fe80727ead1d
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857516"
---
# <a name="inline-functions-c"></a>インライン関数 (C++)

クラス宣言の本体で定義される関数はインライン関数です。

## <a name="example"></a>使用例

次のクラス宣言では、`Account` コンストラクターがインライン関数です。 メンバー関数は、 `GetBalance`、 `Deposit`、および`Withdraw`として指定されていない**inline**がインライン関数として実装することができます。

```cpp
// Inline_Member_Functions.cpp
class Account
{
public:
    Account(double initial_balance) { balance = initial_balance; }
    double GetBalance();
    double Deposit( double Amount );
    double Withdraw( double Amount );
private:
    double balance;
};

inline double Account::GetBalance()
{
    return balance;
}

inline double Account::Deposit( double Amount )
{
    return ( balance += Amount );
}

inline double Account::Withdraw( double Amount )
{
    return ( balance -= Amount );
}
int main()
{
}
```

> [!NOTE]
>  クラス宣言では、関数は**インライン**キーワードを使用せずに宣言されています。 **インライン**キーワードは、クラス宣言で指定できます。結果は同じです。

特定のインライン メンバー関数は、すべてのコンパイル単位で同じ方法で宣言する必要があります。 この制約により、インライン関数は、インスタンス化された関数のように動作します。 また、インライン関数の定義は正確に 1 つだけあることが必要です。

その関数の定義が含まれていない場合、クラス メンバー関数の外部リンケージを既定値、**inline**指定子。 前の例をこれらの関数必要がありますいない明示的に宣言すると、**inline**指定子を使用して**inline**関数の定義、インライン関数を使用すると、します。 ただし、関数として再宣言するされていない**inline**その関数を呼び出した後。

## <a name="inline-__inline-and-__forceinline"></a>インライン、__inline、\__forceinline

**inline**と **_ _inline**指定子、関数が呼び出される適切な各場所に、関数本体のコピーを挿入するようコンパイラに指示します。

挿入 (インライン展開またはインライニングと呼ばれます) は、コンパイラの費用対効果分析により利益があるとわかった場合のみ発生します。 インライン展開では、関数呼び出しのオーバーヘッドが軽減されますが、コード サイズが大きくなるという潜在的なコストがあります。

**__Forceinline**キーワードはコストと利点の分析をオーバーライドし、代わりにプログラマの判断に依存します。 **__Forceinline**を使用する場合は注意が必要です。 **__Forceinline**を使用すると、パフォーマンスが低下するだけでなく、場合によってはパフォーマンスが低下する可能性があります (たとえば、大規模な実行可能ファイルのページングが増加しているため)。

インライン関数を使用すると、関数呼び出しに関連するオーバーヘッドが回避されるため、プログラムを高速化できます。 インライン展開される関数は、標準の関数では使用できない、コードの最適化の対象になります。

インライン展開に関するオプションとキーワードは、インライン展開の対象となる候補をコンパイラに示すだけです。 関数がインライン展開される保証はありません。 **__Forceinline**キーワードを使用している場合でも、特定の関数を強制的にインライン化することはできません。 **/Clr**を使用してコンパイルする場合、関数にセキュリティ属性が適用されていると、コンパイラは関数をインライン化しません。

**inline**キーワードは C++ でのみ使用できます。 **__Inline**および **__forceinline**キーワードは、C とC++の両方で使用できます。 以前のバージョンとの互換性を維持するために、 **_inline**と **_forceinline**は **__inline**のシノニムであり、コンパイラオプション[/Za \(言語拡張を無効にする)](../build/reference/za-ze-disable-language-extensions.md)が指定されていない限り **__forceinline**です。

**inline**キーワードは、インライン展開が優先されることをコンパイラに指示します。 ただし、コンパイラは、コードをインラインで挿入する代わりに、関数の別のインスタンスを作成 (インスタンス化) し、標準の呼び出しリンケージを作成できます。 このようになるのは、次の 2 つの場合です。

- 再帰関数。

- 翻訳単位の別の場所にあるポインターを通じて参照される関数。

これらの理由を妨げる可能性、インライン展開*may 他のユーザーと*、;、コンパイラの裁量でする必要がありますに依存しない、**inline**のためインライン化できません関数指定子。

通常の関数の場合と同様に、インライン関数への引数の評価の順序は定義されていません。 実際には、通常の関数呼び出しプロトコルで渡される引数の評価順序とは異なる場合があります。

[/Ob](../build/reference/ob-inline-function-expansion.md)コンパイラの最適化オプションは、インライン関数の拡張が実際に発生するかどうかを判断するのに役立ちます。

[/Ltcg](../build/reference/ltcg-link-time-code-generation.md)は、ソースコードで要求されたかどうかに関係なく、モジュール間のインライン展開を実行します。

### <a name="example-1"></a>例 1

```cpp
// inline_keyword1.cpp
// compile with: /c
inline int max( int a , int b ) {
   if( a > b )
      return a;
   return b;
}
```

クラスのメンバー関数を使用してインラインで宣言することができます、**inline**キーワードまたはクラス定義内で関数の定義を配置することで。

### <a name="example-2"></a>例 2

```cpp
// inline_keyword2.cpp
// compile with: /EHsc /c
#include <iostream>
using namespace std;

class MyClass {
public:
   void print() { cout << i << ' '; }   // Implicitly inline
private:
   int i;
};
```

**Microsoft 固有の仕様**

**_ _Inline**キーワードは等価**inline**します。

**__Forceinline**でも、コンパイラはすべての状況でコードをインライン化できません。 次の場合、コンパイラは関数をインライン展開できません。

- 関数またはその呼び出し元が /Ob0 (デバッグ ビルドの既定オプション) でコンパイルされる。

- 関数と呼び出し元が、異なる種類の例外処理を使用する (一方は C++ 例外処理、他方は構造化例外処理)。

- 関数に可変個引数リストが含まれている。

- 関数が /Og、/Ox、/O1、または /O2 を指定してコンパイルされていない場合に、インライン アセンブリを使用する。

- 関数は再帰的であり、 **#pragma inline_recursion (on)** を伴いません。 プラグマによって、再帰関数はインライン展開され、既定の深さは 16 呼び出しになります。 インライン展開の深さを減らすには、 [inline_depth](../preprocessor/inline-depth.md)プラグマを使用します。

- 関数が仮想で、仮想的に呼び出される。 仮想関数への直接呼び出しはインライン展開できます。

- プログラムが関数のアドレスを受け取り、関数へのポインターによって呼び出される。 受け取られるアドレスを持っている関数への直接呼び出しはインライン展開できます。

- 関数は、[生](../cpp/naked-cpp.md)の[__declspec](../cpp/declspec.md)修飾子でもマークされます。

コンパイラが **__forceinline**で宣言された関数をインライン化できない場合は、次の場合を除き、レベル1の警告が生成されます。

- 関数は、/Od または/ob0を使用してコンパイルされます。 このような場合、インライン展開は必要ありません。

- 関数は、外部、含まれているライブラリまたは別の翻訳単位で定義されているか、仮想呼び出しターゲットまたは間接呼び出しターゲットです。 コンパイラは、現在の翻訳単位では見つからない非インラインコードを識別できません。

再帰関数は、 [inline_depth](../preprocessor/inline-depth.md)プラグマによって指定された深さにインラインで置き換えることができます。最大で16の呼び出しを行うことができます。 その深さの後、再帰関数の呼び出しは、関数のインスタンスへの呼び出しとして扱われます。  再帰関数がインライン ヒューリスティックによってチェックされる深さは、16 を超えることはできません。 [Inline_recursion](../preprocessor/inline-recursion.md)プラグマは、現在展開されている関数のインライン展開を制御します。 関連情報については、[インライン関数の展開](../build/reference/ob-inline-function-expansion.md)(/Ob) コンパイラオプションに関する説明を参照してください。

**Microsoft 固有の仕様はここまで**

使用しての詳細については、**inline**指定子を参照してください。

- [インラインクラスメンバー関数](../cpp/inline-functions-cpp.md)

- [dllexport と dllimport を使用したインライン C 関数の定義](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>インライン関数を使用する状況

インライン関数は、プライベート データ メンバーにアクセスする関数のような小さな関数に使用するのが最適です。 これらの 1 行または 2 行の "アクセサー" 関数の主な目的は、オブジェクトに関する状態情報を返すことです。短い関数は、関数呼び出しのオーバーヘッドに敏感です。 長い関数は、呼び出すシーケンスと返すシーケンスにかかる時間が相対的に少なく、インライン展開の利点が少なくなります。

`Point` クラスは次のように定義できます。

```cpp
// when_to_use_inline_functions.cpp
class Point
{
public:
    // Define "accessor" functions as
    //  reference types.
    unsigned& x();
    unsigned& y();
private:
    unsigned _x;
    unsigned _y;
};

inline unsigned& Point::x()
{
    return _x;
}
inline unsigned& Point::y()
{
    return _y;
}
int main()
{
}
```

座標の操作がクライアントでこのようなクラスの 2 つのアクセサー関数を指定することは比較的一般的な操作を (`x`と`y`前の例) として**inline**通常を保存します、上のオーバーヘッド。

- 関数呼び出し (パラメーターの引き渡しおよびスタックへのオブジェクトのアドレスの配置を含む)

- 呼び出し元のスタック フレームの保持

- 新しいスタック フレームのセットアップ

- 戻り値のやり取り

- 元のスタック フレームの復元

- Return

## <a name="inline-functions-vs-macros"></a>インライン関数とマクロ

インライン関数はマクロに似ていますが、インライン関数がコンパイラによって解析されるのに対し (関数コードはコンパイル時に呼び出しの時点で展開されるため)、マクロはプリプロセッサによって展開されます。 そのため、これらにはいくつかの重要な違いがあります。

- インライン関数は、通常の関数に適用されるタイプ セーフのすべてのプロトコルに従います。

- インライン関数を指定する点が異なりますとして他の関数と同じ構文を使用して、**inline**関数の宣言でキーワード。

- インライン関数に引数として渡された式は、1 回だけ評価されます。 マクロでは、引数として渡された式が複数回評価される可能性があります。

次の例は、小文字を大文字に変換するマクロを示しています。

```cpp
// inline_functions_macro.c
#include <stdio.h>
#include <conio.h>

#define toupper(a) ((a) >= 'a' && ((a) <= 'z') ? ((a)-('a'-'A')):(a))

int main() {
   char ch;
   printf_s("Enter a character: ");
   ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
//  Sample Input:  xyz
// Sample Output:  Z
```

式 `toupper(getc(stdin))` の目的は、コンソールデバイス (`stdin`) から文字を読み取って、必要に応じて大文字に変換することです。

マクロの実装により、入力文字が "a" 以上であるかどうかを判断するため `getc` が 1 回実行され、さらにその文字が "z" 以下であるかどうかを判断するためもう 1 回実行されます。 入力文字がその範囲にある場合、`getc` が再実行されて、文字が大文字に変換されます。 つまり、このプログラムでは文字を 2 回または 3 回にわたって待機しますが、待機は 1 回だけに抑えるのが本来最適な方法です。

インライン関数を使用すると、このような問題が解消されます。

```cpp
// inline_functions_inline.cpp
#include <stdio.h>
#include <conio.h>

inline char toupper( char a ) {
   return ((a >= 'a' && a <= 'z') ? a-('a'-'A') : a );
}

int main() {
   printf_s("Enter a character: ");
   char ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
```

```Output
Sample Input: a
Sample Output: A
```

## <a name="see-also"></a>参照

[noinline](../cpp/noinline.md)<br/>
[auto_inline](../preprocessor/auto-inline.md)