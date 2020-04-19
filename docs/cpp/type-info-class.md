---
title: type_info Class
ms.date: 11/04/2016
f1_keywords:
- type_info
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
ms.openlocfilehash: b0cddd2c5cc09e77e8733ca88177c3b2223fc8ce
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68242081"
---
# <a name="typeinfo-class"></a>type_info Class

**Type_info**クラスには、プログラム内で、コンパイラによって生成される型情報がについて説明します。 このクラスのオブジェクトは、実質的には型の名前へのポインターを格納します。 **Type_info**クラスでは、または照合順序の 2 つの型の等価性を比較するのに適したエンコード値も格納されます。 型のエンコーディング規則と照合順序については指定されていないため、プログラムによって異なる場合があります。

`<typeinfo>`ヘッダー ファイルを使用するには含めることは、 **type_info**クラス。 インターフェイス、 **type_info**クラスです。

```cpp
class type_info {
public:
    type_info(const type_info& rhs) = delete; // cannot be copied
    virtual ~type_info();
    size_t hash_code() const;
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;
    type_info& operator=(const type_info& rhs) = delete; // cannot be copied
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;
    _CRTIMP_PURE int before(const type_info& rhs) const;
    size_t hash_code() const noexcept;
    _CRTIMP_PURE const char* name() const;
    _CRTIMP_PURE const char* raw_name() const;
};
```

オブジェクトをインスタンス化することはできません、 **type_info**クラスを直接クラスにプライベート コピー コンス トラクターのみがあるためです。 (一時) を構築する唯一の方法**type_info**オブジェクトは、使用する、 [typeid](../cpp/typeid-operator.md)演算子。 代入演算子はプライベートでもあるため、コピーまたはクラスのオブジェクトを代入することはできません**type_info**します。

`type_info::hash_code` 型の値のマッピングに適したハッシュ関数を定義します。 **typeinfo**インデックス値の分布にします。

演算子`==`と`!=`他の等号または不等号の比較に使用できる**type_info**オブジェクトをそれぞれします。

型の照合順序と継承関係には関連性はありません。 使用して、`type_info::before`型の照合順序を決定するメンバー関数。 保証はありませんが`type_info::before`別のプログラムまたは同じプログラムの別の実行で同じ結果が生成されます。 この方法で`type_info::before`アドレスのような`(&)`演算子。

`type_info::name`メンバー関数を返します、`const char*`型の人間が判読できる名前を表す null で終わる文字列にします。 ポイントされたメモリはキャッシュされ、直接解放されることはありません。

`type_info::raw_name`メンバー関数を返します、`const char*`オブジェクトの種類の装飾名を表す null で終わる文字列にします。 実際、名前は保存領域を節約するために、修飾された形式で格納されます。 そのため、この関数より高速`type_info::name`名前を使用する必要がないためです。 によって返される文字列、`type_info::raw_name`関数は比較演算で役に立ちますが、読み取ることができません。 使用して、人間が判読できる文字列が必要な場合、`type_info::name`関数を使用します。

場合にのみ、ポリモーフィックなクラスの型情報が生成された、 [/GR (ランタイム型情報の有効化)](../build/reference/gr-enable-run-time-type-information.md)コンパイラ オプションを指定します。

## <a name="see-also"></a>関連項目

[ランタイム型情報](../cpp/run-time-type-information.md)