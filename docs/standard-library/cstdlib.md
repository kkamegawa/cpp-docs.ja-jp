---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 0b4f24f50c78d9a079e2c7d0c8e3d3c5bfe952c2
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127212"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

C 標準ライブラリヘッダー \<stdlib.h> > をインクルードし、関連`std`する名前を名前空間に追加します。 このヘッダーをインクルードすると、C 標準ライブラリヘッダーの外部リンケージを使用して宣言され`std`た名前が、名前空間で宣言されます。

> [!NOTE]
> \<stdlib.h> > には**wchar_t**型が含まれていません。

## <a name="requirements"></a>要件

**ヘッダー**: \<cstdlib >

**名前空間:** std

## <a name="namespace-and-macros"></a>名前空間とマクロ

```cpp
namespace std {
    using size_t = see definition;
    using div_t = see definition;
    using ldiv_t = see definition;
    using lldiv_t = see definition;
}

#define NULL
#define EXIT_FAILURE
#define EXIT_SUCCESS
#define RAND_MAX
#define MB_CUR_MAX
```

## <a name="exposition-only-functions"></a>Exposition のみの関数

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>Start 関数と終了関数

|関数|説明|
|-|-|
|[_Exit](#_exit)|デストラクターや登録された関数を使用せずにプログラムを終了します。|
|[abort](#abort)|デストラクターを使用せずにプログラムを終了します。|
|[atexit](#atexit)|プログラムの終了のために関数を登録します。|
|[exit](#exit)|スレッドと静的ストレージを使用してオブジェクトを破棄し、制御を返します。|
|[at_quick_exit](#at_quick_exit)|プログラムの終了に引数を指定せずに関数を登録します。|
|[quick_exit](#quick_exit)|プログラムを終了するために、保存されたオブジェクトを使用して関数を登録します。|
|[getenv](#getenv)|「C 標準ライブラリリファレンス」を参照してください。|
|[system](#system)|「C 標準ライブラリリファレンス」を参照してください。|

### <a name="_exit"></a>_Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>コメント

プログラムは、自動、スレッド、または静的ストレージ存続期間のオブジェクトに対してデストラクターを実行せずに`atexit()`終了し、に渡された関数を呼び出さずに終了します。 関数`_Exit`は、シグナルセーフです。

### <a name="abort"></a>取り消し

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>コメント

プログラムは、自動、スレッド、または静的ストレージ存続期間のオブジェクトに対してデストラクターを実行せずに`atexit()`終了し、に渡された関数を呼び出さずに終了します。 関数`abort`は、シグナルセーフです。

### <a name="at_quick_exit"></a>at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>戻り値

登録が成功した場合は0、失敗した場合は0以外の値。

#### <a name="remarks"></a>コメント

関数は、が呼び出されたときに`quick_exit`引数なしで呼び出される関数 func を登録します。 `at_quick_exit()` を呼び出す`at_quick_exit()`と、のすべての`quick_exit`呼び出しが成功しなくなる可能性があります。 これら`at_quick_exit()`の関数は、データの競合を招くことはありません。 が複数のスレッドから呼び出された`at_quick_exit`場合、登録の順序が不確定になることがあります。 登録`at_quick_exit`は登録と`atexit`は別であるため、アプリケーションでは、同じ引数を使用して両方の登録関数を呼び出す必要がある場合があります。 MSVC では、少なくとも32関数の登録がサポートされています。

### <a name="atexit"></a>atexit

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>コメント

関数`atexit()`は、通常のプログラムの終了時に引数なしで呼び出されるように*func*が指す関数を登録します。 へ`atexit()`の呼び出しが失敗する前`exit()`にを呼び出すことはできません。 これら`atexit()`の関数は、データの競合を招くことはありません。

#### <a name="return-value"></a>戻り値

登録が成功した場合は0を返し、失敗した場合は0以外の値を返します。

### <a name="exit"></a>終了

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>コメント

まず、スレッドストレージ存続期間があり、現在のスレッドに関連付けられているオブジェクトが破棄されます。

次に、静的ストレージ存続期間を持つオブジェクトが破棄され`atexit` 、を呼び出すことによって登録される関数が呼び出されます。 が呼び出されると`exit()` 、自動オブジェクトは破棄されません。 関数がスローされた例外の`exit`ハンドラーを提供しないため、コントロールがによって`std::terminate()`呼び出された登録済みの関数を離れる場合は、が呼び出されます。 関数は、登録されるたびに1回呼び出されます。 自動ストレージ存続期間を持つオブジェクトはすべて、自動オブジェクト`main`を含まない関数を持つプログラムで破棄さ`exit()`れ、の呼び出しを実行します。 `main` で`main`キャッチされた例外をスローすることで、このような関数に制御を直接転送できます。

次に、すべての開いている c ストリーム (cstdio > で\<宣言された関数シグネチャによって仲介される) を、書き込まれていないバッファーデータでフラッシュ`tmpfile()`し、開いているすべての c ストリームを閉じ、を呼び出して作成されたすべてのファイルを削除します。

最後に、コントロールがホスト環境に返されます。 *Status*が0または EXIT_SUCCESS の場合、実装によって定義された状態の終了が正常終了として返されます。 MSVC は0の値を返します。 *Status*が EXIT_FAILURE の場合、MSVC は値3を返します。 それ以外の場合、MSVC は*status*パラメーターの値を返します。

### <a name="getenv"></a>getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a>quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>コメント

一般に、へ`at_quick_exit`の呼び出しによって登録される関数は、登録の逆の順序で呼び出されます。 この順序は、他の登録済み関数が既に呼び出された後に登録された関数には適用されません。 `quick_exit`が呼び出されても、オブジェクトは破棄されません。 関数がスローされた例外の`quick_exit`ハンドラーを提供しないため、コントロールがによって`std::terminate()`呼び出された登録済みの関数を離れる場合は、が呼び出されます。 経由`at_quick_exit`で登録された関数は、を呼び出す`quick_exit`スレッドによって呼び出されます。これは、それを登録したスレッドとは異なるスレッドになる可能性があります。 つまり、登録された関数は、スレッドストレージ存続期間を持つオブジェクトの id に依存することはできません。 登録された関数`quick_exit`を`_Exit(status)`呼び出すと、はを呼び出します。 標準のファイルバッファーはフラッシュされません。 関数`quick_exit`は、に登録されている関数が`at_quick_exit`である場合、シグナルセーフです。

### <a name="system"></a>system

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>メモリ割り当て関数

```cpp
// void* aligned_alloc(size_t alignment, size_t size); // Unsupported in MSVC
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
```

### <a name="remarks"></a>コメント

これらの関数には、C 標準ライブラリで指定されたセマンティクスがあります。 MSVC では、 `aligned_alloc`関数はサポートされていません。 C11 は`aligned_alloc()` 、の`free()`Microsoft 実装 () `free()`と互換性のない方法で指定されています。このような方法では、固定された割り当てを処理できなければなりません。

## <a name="numeric-string-conversions"></a>数値文字列の変換

```cpp
double atof(const char* nptr);
int atoi(const char* nptr);
long int atol(const char* nptr);
long long int atoll(const char* nptr);
double strtod(const char* nptr, char** endptr);
float strtof(const char* nptr, char** endptr);
long double strtold(const char* nptr, char** endptr);
long int strtol(const char* nptr, char** endptr, int base);
long long int strtoll(const char* nptr, char** endptr, int base);
unsigned long int strtoul(const char* nptr, char** endptr, int base);
unsigned long long int strtoull(const char* nptr, char** endptr, int base);
```

### <a name="remarks"></a>コメント

これらの関数には、C 標準ライブラリで指定されたセマンティクスがあります。

## <a name="multibyte--wide-string-and-character-conversion-functions"></a>マルチバイト/ワイド文字列および文字変換関数

```cpp
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* pwc, const char* s, size_t n);
int wctomb(char* s, wchar_t wchar);
size_t mbstowcs(wchar_t* pwcs, const char* s, size_t n);
size_t wcstombs(char* s, const wchar_t* pwcs, size_t n);
```

### <a name="remarks"></a>コメント

これらの関数には、C 標準ライブラリで指定されたセマンティクスがあります。

## <a name="algorithm-functions"></a>アルゴリズム関数

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

### <a name="remarks"></a>コメント

これらの関数には、C 標準ライブラリで指定されたセマンティクスがあります。

## <a name="low-quality-random-number-generation-functions"></a>低品質の乱数生成関数

```cpp
int rand();
void srand(unsigned int seed);
```

### <a name="remarks"></a>コメント

これらの関数には、C 標準ライブラリで指定されたセマンティクスがあります。

## <a name="absolute-values"></a>絶対値

```cpp
int abs(int j);
long int abs(long int j);
long long int abs(long long int j);
float abs(float j);
double abs(double j);
long double abs(long double j);
long int labs(long int j);
long long int llabs(long long int j);
```

### <a name="remarks"></a>コメント

これらの関数には、C 標準ライブラリで指定されたセマンティクスがあります。

## <a name="integer-division"></a>整数の除算

```cpp
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>コメント

これらの関数には、C 標準ライブラリで指定されたセマンティクスがあります。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリの概要](../standard-library/cpp-standard-library-overview.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
