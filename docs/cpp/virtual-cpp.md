---
title: virtual (C++)
ms.date: 11/04/2016
f1_keywords:
- virtual_cpp
- virtual
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
ms.openlocfilehash: f68bd2e500ebe16c43ef6c3d7a5aede26421b27d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393910"
---
# <a name="virtual-c"></a>virtual (C++)

**virtual**キーワードは、仮想関数または仮想基底クラスを宣言します。

## <a name="syntax"></a>構文

```
virtual [type-specifiers] member-function-declarator
virtual [access-specifier] base-class-name
```

#### <a name="parameters"></a>パラメーター

*type-specifiers*<br/>
仮想メンバー関数の戻り値の型を指定します。

*member-function-declarator*<br/>
メンバー関数を宣言します。

*access-specifier*<br/>
基底クラスへのアクセスのレベルを定義**public**、**protected**または**private**します。 前に、または後に表示されることができます、**virtual**キーワード。

*base-class-name*<br/>
以前に宣言されたクラス型を識別します。

## <a name="remarks"></a>Remarks

参照してください[仮想関数](../cpp/virtual-functions.md)詳細についてはします。

また、次のキーワードを参照してください:[クラス](../cpp/class-cpp.md)、[プライベート](../cpp/private-cpp.md)、[パブリック](../cpp/public-cpp.md)と[保護](../cpp/protected-cpp.md)します。

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)