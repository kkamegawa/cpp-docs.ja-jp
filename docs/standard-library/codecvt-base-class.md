---
title: codecvt_base クラス
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_base
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
ms.openlocfilehash: 6fca9b2130407b165a7a7bfb1fb2a9ec81774e20
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689885"
---
# <a name="codecvt_base-class"></a>codecvt_base クラス

@No__t_0 と呼ばれる列挙型を定義するために使用される codecvt クラスの基本クラスです。変換の結果を示すためにファセットメンバー関数の戻り値の型として使用されます。

## <a name="syntax"></a>構文

```cpp
class codecvt_base : public locale::facet {
public:
    enum result {ok, partial, error, noconv};
    codecvt_base( size_t _Refs = 0);
    bool always_noconv() const;
    int max_length() const;
    int encoding() const;
    ~codecvt_base()

protected:
    virtual bool do_always_noconv() const;
    virtual int do_max_length() const;
    virtual int do_encoding() const;
};
```

## <a name="remarks"></a>Remarks

クラスは、クラステンプレート[codecvt](../standard-library/codecvt-class.md)のすべての特殊化に共通の列挙体を記述します。 列挙の結果には、次のような [do_in](../standard-library/codecvt-class.md#do_in) または [do_out](../standard-library/codecvt-class.md#do_out) からの可能な戻り値が示されます。

- 内部と外部の文字エンコーディングの変換が成功した場合に `ok` します。

- 変換先が変換に成功するのに十分な大きさでない場合は `partial`。

- ソースシーケンスの形式が間違っている場合は `error` します。

- 関数で変換が行われない場合は、`noconv`。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
