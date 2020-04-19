---
title: ctype&lt;char&gt; クラス
ms.date: 11/04/2016
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
helpviewer_keywords:
- ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
ms.openlocfilehash: 08bf2c5c814eaed7b409295fcf50c66577f6a5d9
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688158"
---
# <a name="ctypeltchargt-class"></a>ctype&lt;char&gt; クラス

クラスは **、char 型**に `ctype\<CharType>` クラステンプレートの明示的な特殊化であり、 **char**型の文字のさまざまなプロパティを特徴付けるためにロケールファセットとして使用できるオブジェクトを記述します。

## <a name="syntax"></a>構文

```cpp
template <>
class ctype<char>
: public ctype_base
{
public:
    typedef char _Elem;
    typedef _Elem char_type;
    bool is(
    mask _Maskval,
    _Elem _Ch) const;

    const _Elem* is(
    const _Elem* first,
    const _Elem* last,
    mask* dest) const;

    const _Elem* scan_is(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    const _Elem* scan_not(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    _Elem tolower(
    _Elem _Ch) const;

    const _Elem* tolower(
    _Elem* first,
    const _Elem* last) const;

    _Elem toupper(
    _Elem _Ch) const;

    const _Elem* toupper(
    _Elem* first,
    const _Elem* last) const;

    _Elem widen(
    char _Byte) const;

    const _Elem* widen(
    const char* first,
    const char* last,
    _Elem* dest) const;

    const _Elem* _Widen_s(
    const char* first,
    const char* last,
    _Elem* dest,
    size_t dest_size) const;

    _Elem narrow(
    _Elem _Ch,
    char _Dflt = '\0') const;

    const _Elem* narrow(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest) const;

    const _Elem* _Narrow_s(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest,
    size_t dest_size) const;

    static locale::id& id;
    explicit ctype(
    const mask* _Table = 0,
    bool _Deletetable = false,
    size_t _Refs = 0);

protected:
    virtual ~ctype();
//other protected members
};
```

## <a name="remarks"></a>Remarks

明示的な特殊化は、いくつかの点でクラステンプレートとは異なります。

- Ctype マスクテーブルの最初の要素へのポインター (型 `ctype_base::mask` の UCHAR_MAX + 1 要素の配列) を格納するクラス ctype < `char` > のオブジェクト。 ctype\< **Elem**> オブジェクトが破棄されるとき、(`operator delete[]` を利用して) 配列を削除するかどうかを示すブール値も格納します。

- 唯一のパブリックコンストラクターを使用すると、`tab`、ctype マスクテーブル、`del` を指定できます。ブール値オブジェクトは、ctype < `char` > オブジェクトが破棄されたときに配列を削除する場合は true、参照カウントパラメーター参照にも指定できます。

- プロテクトメンバー関数 `table` は、格納されている ctype マスクテーブルを返します。

- @No__t_0 静的メンバーオブジェクトは、ctype マスクテーブル内の要素の最小数を指定します。

- プロテクト静的メンバー関数 `classic_table` ("C" ロケールに適した ctype マスクテーブルを返します)。

- 保護されている仮想メンバー関数 [do_is](../standard-library/ctype-class.md#do_is)、[do_scan_is](../standard-library/ctype-class.md#do_scan_is)、[do_scan_not](../standard-library/ctype-class.md#do_scan_not) はありません。 それに対応するパブリック メンバー関数が同等の操作を実行します。

メンバー関数の [do_narrow](../standard-library/ctype-class.md#do_narrow) と [do_widen](../standard-library/ctype-class.md#do_widen) は、要素を変更せずにコピーします。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="see-also"></a>関連項目

[facet クラス](locale-class.md#facet_class)\
[ctype_base クラス](../standard-library/ctype-base-class.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
