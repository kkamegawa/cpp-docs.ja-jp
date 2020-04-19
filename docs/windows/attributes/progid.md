---
title: progid (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.progid
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
ms.openlocfilehash: d529d7362dc62207cfd72576159f560a3e04c221
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514250"
---
# <a name="progid"></a>progid

COM オブジェクトの ProgID を指定します。

## <a name="syntax"></a>構文

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>パラメーター

*name*<br/>
オブジェクトを表す ProgID。

Progid には、COM/ActiveX オブジェクトを識別するために使用されるクラス識別子 (CLSID) のユーザーが判読できるバージョンが存在します。

## <a name="remarks"></a>Remarks

**Progid** C++属性では、COM オブジェクトの progid を指定できます。 ProgID は、name1. *name2.* という形式になります。 ProgID の*バージョン*を指定しない場合、既定のバージョンは1になります。 *Name1*を指定しない場合、既定の名前は*classname. classname*になります。 **Progid**を指定せずにを指定`vi_progid`した場合、 *name1*はから`vi_progid`取得され、(次の連続番号) バージョンが追加されます。

**Progid**を使用する属性ブロックが**uuid**も使用していない場合、コンパイラはレジストリを調べて、指定された**progid**に**uuid**が存在するかどうかを確認します。 **Progid**が指定されていない場合は、バージョン (コクラスを作成する場合はコクラス名) が**progid**の生成に使用されます。

**progid**は`coclass`属性を意味します。つまり、 **progid**を指定した場合は、progid 属性`coclass`と**progid**属性を指定することと同じです。

**Progid**属性により、指定した名前でクラスが自動的に登録されます。 生成された .idl ファイルには**progid**値が表示されません。

ATL を使用するプロジェクト内でこの属性を使用すると、属性の動作が変更されます。 上記の動作に加えて、この属性で指定された情報は、 `GetProgID` `coclass`属性によって挿入される関数で使用されます。 詳細については、「 [coclass](coclass.md)属性」を参照してください。

## <a name="example"></a>例

**Progid**の使用例については、[コクラス](coclass.md)の例を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**、**構造体**|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[ProgID キー](/windows/win32/com/-progid--key)
