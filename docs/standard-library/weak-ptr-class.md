---
title: weak_ptr クラス
ms.date: 07/29/2019
f1_keywords:
- memory/std::weak_ptr
- memory/std::weak_ptr::element_type
- memory/std::weak_ptr::expired
- memory/std::weak_ptr::lock
- memory/std::weak_ptr::owner_before
- memory/std::weak_ptr::reset
- memory/std::weak_ptr::swap
- memory/std::weak_ptr::use_count
- memory/std::weak_ptr::operator=
helpviewer_keywords:
- std::weak_ptr [C++]
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
ms.assetid: 2db4afb2-c7be-46fc-9c20-34ec2f8cc7c2
ms.openlocfilehash: 2591c4cd124f83085235828d3eb29ab1a90d894a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684085"
---
# <a name="weak_ptr-class"></a>weak_ptr クラス

関連付けの弱いポインターをラップします。

## <a name="syntax"></a>構文

```cpp
template<class T> class weak_ptr;
```

### <a name="parameters"></a>パラメーター

*T* \
ウィーク ポインターによって制御される型。

## <a name="remarks"></a>Remarks

クラステンプレートは、1つまたは複数の[shared_ptr](shared-ptr-class.md)オブジェクトによって管理されるリソースを指すオブジェクトを表します。 リソースをポイントする `weak_ptr` オブジェクトは、リソースの参照カウントに影響しません。 リソースを管理する最後の `shared_ptr` オブジェクトが破棄されると、そのリソースを指し示す `weak_ptr` オブジェクトがある場合でも、リソースは解放されます。 この動作は、データ構造の循環を避けるために不可欠です。

`weak_ptr` オブジェクトは、リソースを所有する `shared_ptr` オブジェクトから構築された場合や、リソースを指し示す `weak_ptr` オブジェクトから構築された場合、またはリソースが [operator=](#op_eq) を使って割り当てられた場合に、そのリソースを指し示します。 @No__t_0 オブジェクトは、そのオブジェクトが指しているリソースへの直接アクセスを提供しません。 そのリソースを使用する必要があるコードは、メンバー関数 [lock](#lock) を呼び出すことによって作成された、そのリソースを所有する `shared_ptr` オブジェクトを介してそのリソースを使用します。 リソースを所有するすべての `shared_ptr` オブジェクトが破棄されているため、`weak_ptr` オブジェクトの有効期限が切れています。 有効期限の切れた `weak_ptr` オブジェクトで `lock` を呼び出すと、空の shared_ptr オブジェクトが作成されます。

空の weak_ptr オブジェクトは、リソースを指しておらず、コントロールブロックも持ちません。 そのメンバー関数 `lock` は、空の shared_ptr オブジェクトを返します。

循環は、`shared_ptr` オブジェクトによって制御される複数のリソースで、相互に参照し合う `shared_ptr` オブジェクトが保持されているときに発生します。 たとえば、3 つの要素から成るリンク リストがあるとします。先頭のノード `N0` が 2 番目のノード `N1` を所有する `shared_ptr` オブジェクトを保持し、2 番目のノードが 3 番目のノード `N2` を所有する `shared_ptr` オブジェクトを保持し、次に、3 番目のノードが先頭のノード `N0` を所有する `shared_ptr` オブジェクトを保持しているとすると、ループが閉じた状態になり、このリストは循環リンク リストになります。 この場合、参照カウントはゼロにならず、サイクル内のノードは解放されません。 この循環を解消するためには、最後のノード `N2` が、`shared_ptr` オブジェクトではなく、`N0` を指し示す `weak_ptr` オブジェクトを保持する必要があります。 @No__t_0 オブジェクトは所有していないため `N0` `N0` の参照カウントには影響しません。また、プログラムのヘッドノードへの最後の参照が破棄されると、リスト内のノードも破棄されます。

## <a name="members"></a>メンバー

|||
|-|-|
| **コンストラクター** | |
|[weak_ptr](#weak_ptr)|`weak_ptr` を構築します。|
| **デストラクター** | |
|[~ weak_ptr](#tilde-weak_ptr)|`weak_ptr` を構築します。|
| **Typedefs** | |
|[element_type](#element_type)|要素の型。|
| **メンバー関数** | |
|[expired](#expired)|所有権の有効期限が切れているかどうかをテストします。|
|[lock](#lock)|リソースの排他的所有権を取得します。|
|[owner_before](#owner_before)|この `weak_ptr` が、指定されたポインターの前 (またはそれより小さい) に順序付けされている場合は**true**を返します。|
|[reset](#reset)|所有されたリソースを解放します。|
|[swap](#swap)|2 つの `weak_ptr` オブジェクトを交換します。|
|[use_count](#use_count)|@No__t_0 オブジェクトの数をカウントします。|
| **演算子** | |
|[operator=](#op_eq)|所有されたリソースを置換します。|

## <a name="element_type"></a>element_type

要素の型。

```cpp
typedef T element_type; // through C++17
using element_type = remove_extent_t<T>; // C++20
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `T` のシノニムです。

### <a name="example"></a>例

```cpp
// std__memory__weak_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::weak_ptr<int>::element_type val = *wp0.lock();

    std::cout << "*wp0.lock() == " << val << std::endl;

    return (0);
}
```

```Output
*wp0.lock() == 5
```

## <a name="expired"></a>終了

所有権の有効期限が切れているかどうか、つまり、参照先のオブジェクトが削除されたかどうかをテストします。

```cpp
bool expired() const noexcept;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、`*this` の有効期限が切れている場合は**true** 、それ以外の場合は**false**を返します。

### <a name="example"></a>例

```cpp
// std__memory__weak_ptr_expired.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="lock"></a>制限

リソースの所有権を共有する `shared_ptr` を取得します。

```cpp
shared_ptr<T> lock() const noexcept;
```

### <a name="remarks"></a>Remarks

@No__t_1 の有効期限が切れた場合、このメンバー関数は空の[shared_ptr](shared-ptr-class.md)オブジェクトを返します。それ以外の場合は、`*this` が指すリソースを所有する `shared_ptr<T>` オブジェクトを返します。 @No__t_0 のアトミック実行に相当する値を返します。

### <a name="example"></a>例

```cpp
// std__memory__weak_ptr_lock.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="op_eq"></a>operator =

所有されたリソースを置換します。

```cpp
weak_ptr& operator=(const weak_ptr& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const weak_ptr<Other>& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const shared_ptr<Other>& ptr) noexcept;
```

### <a name="parameters"></a>パラメーター

*その他の*\
引数の共有ポインターまたはウィークポインターによって制御される型。

*ptr* \
コピーする弱ポインターまたは共有ポインター。

### <a name="remarks"></a>Remarks

すべての演算子は、現在 `*this` によってポイントされているリソースを解放し、 *ptr*によって指定されたリソースの所有権を `*this` に割り当てます。 操作が失敗した場合、`*this` は変更されません。 各演算子には、`weak_ptr(ptr).swap(*this)` と同等の効果があります。

### <a name="example"></a>例

```cpp
// std__memory__weak_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::shared_ptr<int> sp1(new int(10));
    wp0 = sp1;
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::weak_ptr<int> wp1;
    wp1 = wp0;
    std::cout << "*wp1.lock() == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*wp0.lock() == 5
*wp0.lock() == 10
*wp1.lock() == 10
```

## <a name="owner_before"></a>owner_before

この `weak_ptr` が、指定されたポインターの前 (またはそれより小さい) に順序付けされている場合は**true**を返します。

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr) const noexcept;

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr) const noexcept;
```

### <a name="parameters"></a>パラメーター

*ptr* \
@No__t_0 または `weak_ptr` への左辺値参照。

### <a name="remarks"></a>Remarks

テンプレートメンバー関数は、 *ptr*の前に `*this` が順序付けされている場合に**true**を返します。

## <a name="reset"></a>解除

所有されているリソースを解放します。

```cpp
void reset() noexcept;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、`*this` によってポイントされているリソースを解放し、`*this` を空の `weak_ptr` オブジェクトに変換します。

### <a name="example"></a>例

```cpp
// std__memory__weak_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp(new int(5));
    std::weak_ptr<int> wp(sp);
    std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    wp.reset();
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    return (0);
}
```

```Output
*wp.lock() == 5
wp.expired() == false
wp.expired() == true
```

## <a name="swap"></a>フォト

2 つの `weak_ptr` オブジェクトを交換します。

```cpp
void swap(weak_ptr& wp) noexcept;
```

また、特殊化も含まれています。

```cpp
template<class T>
void swap(weak_ptr<T>& a, weak_ptr<T>& b) noexcept;
```

### <a name="parameters"></a>パラメーター

*wp* \
交換するウィーク ポインター。

### <a name="remarks"></a>Remarks

@No__t_0 の後、もともと `*this` によって参照されていたリソースは、 *wp*によってポイントされ、もともと*wp*によってポイントされていたリソースは `*this` によってポイントされます。 関数は、2つのリソースの参照カウントを変更せず、例外もスローしません。 テンプレートの特殊化の効果は、`a.swap(b)` に相当します。

### <a name="example"></a>例

```cpp
// std__memory__weak_ptr_swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5

*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="use_count"></a>use_count

共有リソースを所有している `shared_ptr` オブジェクトの数をカウントします。

```cpp
long use_count() const noexcept;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、`*this` が指し示すリソースを所有する `shared_ptr` オブジェクトの数を返します。

### <a name="example"></a>例

```cpp
// std__memory__weak_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    return (0);
}
```

```Output
wp.use_count() == 1
wp.use_count() == 2
```

## <a name="weak_ptr"></a>weak_ptr

`weak_ptr` を構築します。

```cpp
constexpr weak_ptr() noexcept;

weak_ptr(const weak_ptr& wp) noexcept;

weak_ptr(weak_ptr&& wp) noexcept;

template <class Other>
weak_ptr(const weak_ptr<Other>& wp) noexcept;

template <class Other>
weak_ptr(weak_ptr<Other>&& sp) noexcept;

template <class Other>
weak_ptr(const shared_ptr<Other>& sp) noexcept;
```

### <a name="parameters"></a>パラメーター

*その他の*\
引数の共有ポインターまたはウィーク ポインターによって制御される型。 _他の \*_ が `element_type*` と互換性がない限り、これらのコンストラクターはオーバーロードの解決に関与しません。

*wp* \
コピーするウィーク ポインター。

*sp* \
コピーする共有ポインター。

### <a name="remarks"></a>Remarks

既定のコンストラクターは、空の `weak_ptr` オブジェクトを構築します。 引数ポインターが空の場合、引数を受け取るコンストラクターはそれぞれ、空の `weak_ptr` オブジェクトを構築します。 それ以外の場合は、引数で指定されたリソースを指す `weak_ptr` オブジェクトを構築します。 共有オブジェクトの参照カウントは変更されません。

### <a name="example"></a>例

```cpp
// std__memory__weak_ptr_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp0;
    std::cout << "wp0.expired() == " << std::boolalpha
        << wp0.expired() << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp1(sp1);
    std::cout << "*wp1.lock() == "
        << *wp1.lock() << std::endl;

    std::weak_ptr<int> wp2(wp1);
    std::cout << "*wp2.lock() == "
        << *wp2.lock() << std::endl;

    return (0);
}
```

```Output
wp0.expired() == true
*wp1.lock() == 5
*wp2.lock() == 5
```

## <a name="tilde-weak_ptr"></a>~ weak_ptr

`weak_ptr` を破棄します。

```cpp
~weak_ptr();
```

### <a name="remarks"></a>Remarks

デストラクターは、この `weak_ptr` を破棄しますが、格納されているポインターが指すオブジェクトの参照カウントには影響しません。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](cpp-standard-library-header-files.md)\
[\<memory>](memory.md)\
[shared_ptr クラス](shared-ptr-class.md)
