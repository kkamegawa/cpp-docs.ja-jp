---
title: Platform::AccessDeniedException クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::AccessDeniedException
- VCCORLIB/Platform::AccessDeniedException::AccessDeniedException
helpviewer_keywords:
- Platform::AccessDeniedException
ms.assetid: 6ae2155b-7b16-4587-8d2d-da05eab4c7e9
ms.openlocfilehash: 4abbac977a256ff27f99caaf77393450d3ccf858
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161772"
---
# <a name="platformaccessdeniedexception-class"></a>Platform::AccessDeniedException クラス

リソースや機能へのアクセスが拒否されるとスローされます。

## <a name="syntax"></a>構文

```cpp
public ref class AccessDeniedException : COMException,    IException,    IPrintable,   IEquatable
```

### <a name="remarks"></a>Remarks

この例外にヒットした場合は、適切な機能を要求したこと、およびアプリのパッケージ マニフェストで必要な宣言を行ったことを確認します。 詳細については、「 [COMException](../cppcx/platform-comexception-class.md) 」クラスを参照してください。

### <a name="requirements"></a>必要条件

**最小値には、クライアントがサポートされています。** Windows 8

**最小値には、サーバーがサポートされています。** Windows Server 2012

**名前空間:** プラットフォーム

**メタデータ:** platform.winmd

## <a name="see-also"></a>関連項目

[Platform::COMException クラス](../cppcx/platform-comexception-class.md)
