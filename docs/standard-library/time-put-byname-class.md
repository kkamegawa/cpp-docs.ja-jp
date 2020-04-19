---
title: time_put_byname クラス
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put_byname
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
ms.openlocfilehash: 4471c0df352a4d40d863ac36f0245cf8194f588c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685467"
---
# <a name="time_put_byname-class"></a>time_put_byname クラス

派生クラステンプレートは、型 `time_put` \< CharType, OutputIterator > のロケールファセットとして使用できるオブジェクトを表します。

## <a name="syntax"></a>構文

```cpp
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```

### <a name="parameters"></a>パラメーター

*@No__t_1*
ロケール名。

*Refs \ (_c)*
最初の参照数。

## <a name="remarks"></a>Remarks

その動作は、[名前付き](../standard-library/locale-class.md#name)ロケール*名*によって決まります。 各コンストラクターは、 [time_put](../standard-library/time-put-class.md#time_put) \<CharType, OutputIterator > (`_Refs`) を使用して、その基本オブジェクトを初期化します。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
