---
title: numpunct_byname クラス
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::numpunct_byname
helpviewer_keywords:
- numpunct_byname class
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
ms.openlocfilehash: da9259df8c527e44a4adea3a53be31b3c3ffc10b
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687603"
---
# <a name="numpunct_byname-class"></a>numpunct_byname クラス

派生クラステンプレートは、特定のロケールの `numpunct` ファセットとして使用できるオブジェクトを表します。このオブジェクトは、数値式およびブール式の書式設定と区切り記号を有効にします。

## <a name="syntax"></a>構文

```cpp
template <class CharType>
class numpunct_byname : public numpunct<Elem> {
public:
    explicit numpunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit numpunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~numpunct_byname();

};
```

## <a name="remarks"></a>Remarks

その動作は [名前付きの](../standard-library/locale-class.md#name)ロケール `_Locname` で決まります。 コンストラクターは、[numpunct](../standard-library/numpunct-class.md#numpunct)\<CharType>( `_Refs`) を使用して、その基本オブジェクトを初期化します。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
