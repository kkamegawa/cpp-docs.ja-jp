---
title: Platform::SizeT 値クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
ms.openlocfilehash: 7f81cb9e1fc2ef7a74cb3878c369e4d7d14e3d90
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330142"
---
# <a name="platformsizet-value-class"></a>Platform::SizeT 値クラス

オブジェクトのサイズを表します。 SizeT は符号なしのデータ型です。

## <a name="syntax"></a>構文

```cpp
public ref class SizeT sealed : ValueType
```

### <a name="members"></a>メンバー

|メンバー|説明|
|------------|-----------------|
|[SizeT::SizeT コンストラクター](#ctor)|指定された値で、クラスの新しいインスタンスを初期化します。|

### <a name="requirements"></a>必要条件

**最小値には、クライアントがサポートされています。** Windows 8

**最小値には、サーバーがサポートされています。** Windows Server 2012

**名前空間:** プラットフォーム

**メタデータ:** platform.winmd

## <a name="ctor"></a>  Sizet::sizet コンス トラクター

指定された値を持つ SizeT の新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
SizeT( uint32 value1 );   SizeT( void* value2 );
```

### <a name="parameters"></a>パラメーター

*value1*<br/>
符号なし 32 ビット値。

*value2*<br/>
符号なし 32 ビット値へのポインター。

## <a name="see-also"></a>関連項目

[プラットフォーム名前空間](../cppcx/platform-namespace-c-cx.md)
