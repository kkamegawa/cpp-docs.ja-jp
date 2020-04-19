---
title: collate_byname クラス
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: 3e9a256ac7bdb5f6d077746fe2a08990ed41e931
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688268"
---
# <a name="collate_byname-class"></a>collate_byname クラス

特定のロケールの collate ファセットとして使用できるオブジェクトを記述する派生クラステンプレート。文字列の並べ替え規則に関するカルチャ領域に固有の情報を取得できます。

## <a name="syntax"></a>構文

```cpp
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```

### <a name="parameters"></a>パラメーター

*@No__t_1*
名前付きのロケール。

*Refs \ (_c)*
最初の参照数。

## <a name="remarks"></a>Remarks

クラステンプレートは、 [collate](../standard-library/collate-class.md#collate) \<CharType > 型の[ロケールファセット](../standard-library/locale-class.md#facet_class)として使用できるオブジェクトを表します。 その動作は、[名前付き](../standard-library/locale-class.md#name)ロケール*名*によって決まります。 各コンストラクターは、[collate](../standard-library/collate-class.md#collate)\<CharType>( `_Refs`) を使用して、その基本オブジェクトを初期化します。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
