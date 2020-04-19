---
title: export (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 771bfdfe4eab2acf31e97a606795066e8938a8a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501604"
---
# <a name="export"></a>export

データ構造を .idl ファイルに配置します。

## <a name="syntax"></a>構文

```cpp
[export]
```

## <a name="remarks"></a>Remarks

**Export** C++属性を指定すると、データ構造が .idl ファイルに配置され、任意の言語で使用できるようにするバイナリ互換形式で、タイプライブラリで使用できるようになります。

クラスにパブリックメンバーのみ (**構造体**と同等) がある場合でも、**エクスポート**属性をクラスに適用することはできません。

名前のない**列挙型**または**構造体**をエクスポートすると、名前の先頭に名前が**付い**ていない<em>x</em>が付けられます。ここで、 *x*は連番です。

エクスポートに有効な typedef は、基本型、構造体、共用体、列挙型、または型識別子です。  詳細については、「 [typedef](/windows/win32/Midl/typedef) 」を参照してください。

## <a name="example"></a>例

**Export**属性の使用方法を次のコードに示します。

```cpp
// cpp_attr_ref_export.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**union**、 **typedef**、 **enum**、 **struct**、または**interface**|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[コンパイラ属性](compiler-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)