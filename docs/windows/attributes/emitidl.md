---
title: emitidl (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.emitidl
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
ms.openlocfilehash: 6c4055e0f14bced1e5047fc502a4bf274126f804
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409656"
---
# <a name="emitidl"></a>emitidl

後続のすべての IDL 属性が処理され、生成された .idl ファイル内に配置するかどうかを指定します。

## <a name="syntax"></a>構文

```cpp
[ emitidl(state, defaultimports=boolean) ];
```

### <a name="parameters"></a>パラメーター

*state*<br/>
これらの使用可能な値のいずれか: `true`、 `false`、 `forced`、 `restricted`、 `push`、または`pop`します。

- 場合`true`、ソース コード ファイルで検出された IDL カテゴリ属性は、生成された .idl ファイルに配置されます。 既定の設定は、この**emitidl**します。

- 場合`false`、ソース コード ファイルで検出された IDL カテゴリ属性は、生成された .idl ファイル内に配置されていません。

- 場合`restricted`、IDL 属性のないファイルを[モジュール](module-cpp.md)属性。 コンパイラは、.idl ファイルを生成しません。

- 場合`forced`、後ろに続くオーバーライド`restricted`属性には、ファイルが必要です、`module`属性 IDL がある場合は、ファイルの属性します。

- `push` 現在を保存することができます**emitidl**内部へ設定**emitidl**スタック、および`pop`設定できます**emitidl**にどのような値は、内部の上部にある、**emitidl**スタック。

`defaultimports=`*ブール*\(省略可能)

- 場合*ブール*は**true**docobj.idl が生成された .idl ファイルにインポートされます。 また、.idl ファイルと同じ名前、.h ファイルする場合`#include`、.h ファイルと同じディレクトリ内に、ソース コードが見つかった後、その .idl ファイルの import ステートメントが生成された .idl ファイルに含まれています。

- 場合*ブール*は**false**docobj.idl が生成された .idl ファイルにインポートされていません。 .Idl ファイルを明示的にインポートする必要があります[インポート](import.md)します。

## <a name="remarks"></a>Remarks

後に、 **emitidl** C++ 属性がソース コード ファイルで発生した、IDL カテゴリ属性は、生成された .idl ファイルに配置されます。 存在する場合ありません**emitidl**属性に、ソース コード ファイル内の IDL 属性は、生成された .idl ファイルに出力します。

複数存在することは**emitidl**ソース コード ファイル内の属性。 場合`[emitidl(false)];`が後ろに続くなしでファイルに発生した`[emitidl(true)];`、生成された .idl ファイルの属性は処理されません。

コンパイラが、新しいファイルを検出するたびに**emitidl**に暗黙的に設定されている**true**します。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|任意の場所|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[コンパイラ属性](compiler-attributes.md)<br/>
[スタンドアロン属性](stand-alone-attributes.md)
