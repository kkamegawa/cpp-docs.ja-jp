---
title: static_assert
ms.date: 07/29/2019
f1_keywords:
- static_assert_cpp
helpviewer_keywords:
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
ms.openlocfilehash: 4ac79c23379dd1bf1c85521fdf0c28947d3b7ab9
ms.sourcegitcommit: 20a1356193fbe0ddd1002e798b952917eafc3439
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661586"
---
# <a name="staticassert"></a>static_assert

コンパイル時にソフトウェアのアサーションをテストします。 指定された定数式が FALSE の場合、指定したメッセージが指定されている場合はコンパイラによって表示され、コンパイルはエラー C2338 で失敗します。それ以外の場合、宣言は無効です。

## <a name="syntax"></a>構文

```
static_assert( constant-expression, string-literal );

static_assert( constant-expression ); // C++17 (Visual Studio 2017 and later)
```

#### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*constant-expression*|ブール型に変換できる整数定数式。<br /><br /> 評価された式が 0 (false) の場合は、*文字列リテラル*パラメーターが表示され、コンパイルはエラーで失敗します。 式が0以外 (true) の場合、 **static_assert**宣言は無効です。|
|*string-literal*|*定数式*のパラメーターが0の場合に表示されるメッセージ。 メッセージは、コンパイラの[基本文字セット](../c-language/ascii-character-set.md)内の文字の文字列です。つまり、[マルチバイト文字またはワイド文字](../c-language/multibyte-and-wide-characters.md)ではありません。|

## <a name="remarks"></a>Remarks

**Static_assert**宣言の*定数式*のパラメーターは、ソフトウェアの*アサーション*を表します。 ソフトウェアのアサーションは、プログラムの特定位置にある true となるはずの条件を指定します。 条件が true の場合、 **static_assert**宣言は無効です。 条件が false の場合、アサーションは失敗し、コンパイラは*文字列リテラル*パラメーターにメッセージを表示し、コンパイルはエラーで失敗します。 Visual Studio 2017 以降では、文字列リテラルパラメーターは省略可能です。

**Static_assert**宣言は、コンパイル時にソフトウェアのアサーションをテストします。 これに対し、 [Assert マクロと _assert 関数および _wassert 関数](../c-runtime-library/reference/assert-macro-assert-wassert.md)は、実行時にソフトウェアアサーションをテストし、領域または時間で実行時のコストを発生させることになります。 **Static_assert**宣言は、テンプレート引数を*定数式*パラメーターに含めることができるため、テンプレートをデバッグする場合に特に便利です。

コンパイラは、宣言が検出されたときに構文エラーの**static_assert**宣言を調べます。 コンパイラは、テンプレートパラメーターに依存していない場合、*定数式*パラメーターを直ちに評価します。 それ以外の場合、コンパイラは、テンプレートがインスタンス化されるときに*定数式*パラメーターを評価します。 その結果、コンパイラは、宣言を検出したときに一度、テンプレートがインスタンス化されたときに再度、診断メッセージを発行することがあります。

**Static_assert**キーワードは、名前空間、クラス、またはブロックスコープで使用できます。 ( **Static_assert**キーワードは、プログラムに新しい名前が導入されていない場合でも、名前空間のスコープで使用できるため、技術的には宣言です)。

## <a name="description"></a>説明

次の例では、 **static_assert**宣言に名前空間スコープが含まれています。 コンパイラは `void *` 型のサイズがわかっているので、式は直ちに評価されます。

## <a name="example"></a>例

```cpp
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");
```

## <a name="description"></a>説明

次の例では、 **static_assert**宣言にクラススコープが含まれています。 **Static_assert**は、テンプレートパラメーターが、 *plain old data* (ポッド) 型であることを確認します。 コンパイラは、宣言されているときに**static_assert**宣言を調べますが、で`basic_string` `main()`クラステンプレートがインスタンス化されるまで、*定数式*のパラメーターは評価されません。

## <a name="example"></a>例

```cpp
#include <type_traits>
#include <iosfwd>
namespace std {
template <class CharT, class Traits = std::char_traits<CharT> >
class basic_string {
    static_assert(std::is_pod<CharT>::value,
                  "Template argument CharT must be a POD type in class template basic_string");
    // ...
    };
}

struct NonPOD {
    NonPOD(const NonPOD &) {}
    virtual ~NonPOD() {}
};

int main()
{
    std::basic_string<char> bs;
}
```

## <a name="description"></a>説明

次の例では、 **static_assert**宣言にブロックスコープが含まれています。 **Static_assert**は、vmpage 構造のサイズがシステムの仮想メモリ pagesize と同じであることを確認します。

## <a name="example"></a>例

```cpp
#include <sys/param.h> // defines PAGESIZE
class VMMClient {
public:
    struct VMPage { // ...
           };
    int check_pagesize() {
    static_assert(sizeof(VMPage) == PAGESIZE,
        "Struct VMPage must be the same size as a system virtual memory page.");
    // ...
    }
// ...
};
```

## <a name="see-also"></a>関連項目

[アサーションとユーザー指定のメッセージ (C++)](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
[#error ディレクティブ (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[assert マクロ、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[[テンプレート]](../cpp/templates-cpp.md)<br/>
[ASCII 文字セット](../c-language/ascii-character-set.md)<br/>
[宣言と定義](declarations-and-definitions-cpp.md)