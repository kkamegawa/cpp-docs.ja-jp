---
title: Platform::Metadata 名前空間
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata
helpviewer_keywords:
- Platform::Metadata Namespace
ms.assetid: e3e114d8-a4b0-47f0-865a-9ce9d7212e86
ms.openlocfilehash: 9626b3a9d28d28fd52a0d2295af8fda8855cd90c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387605"
---
# <a name="platformmetadata-namespace"></a>Platform::Metadata 名前空間

この名前空間には、型の宣言を変更する属性が含まれます。

## <a name="syntax"></a>構文

```cpp
namespace Platform {
   namespace Metadata {
}}
```

### <a name="members"></a>メンバー

この名前空間は内部使用のためのものですが、ブラウザーでこの名前空間の次のメンバーを表示できます。

|名前|コメント|
|----------|------------|
|属性|属性の基底クラス。|
|[Platform::Metadata::DefaultMemberAttribute 属性](../cppcx/platform-metadata-defaultmemberattribute-attribute.md)|使用できる複数のオーバーロード関数から呼び出す、推奨される関数を示します。|
|[Platform::Metadata::FlagsAttribute Attribute (Platform::Metadata::FlagsAttribute 属性)](../cppcx/platform-metadata-flagsattribute-attribute.md)フラグ|列挙体を、ビット フィールドの列挙体としてを宣言します。<br /><br /> 次の例は、 `Flags` 属性を列挙体に適用する方法を示しています。<br /><br /> `[Flags] enum class MyEnumeration { enumA = 1, enumB = 2, enumC = 3}`|
|[Platform::Metadata::RuntimeClassNameAttribute](../cppcx/platform-metadata-runtimeclassname.md)|プライベート ref クラスには有効なランタイム クラス名があることを確認します。|

## <a name="inheritance-hierarchy"></a>継承階層

`Platform`

### <a name="requirements"></a>必要条件

**メタデータ:** platform.winmd

**名前空間:** Platform::metadata

## <a name="see-also"></a>関連項目

[プラットフォーム Namespace](platform-namespace-c-cx.md)
