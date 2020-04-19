---
title: Platform::DisconnectedException クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::DisconnectedException
- VCCORLIB/Platform::DisconnectedException::DisconnectedException
helpviewer_keywords:
- Platform::DisconnectedException
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
ms.openlocfilehash: 56276a7d09cc82e05886c2c67a4784993083adb5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387618"
---
# <a name="platformdisconnectedexception-class"></a>Platform::DisconnectedException クラス

存在しなくなった COM サーバーを COM プロキシ オブジェクトが参照しようとするとスローされます。

## <a name="syntax"></a>構文

```
public ref class DisconnectedException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Remarks

クラス A が別のプロセスにある他のクラス (クラス B) を参照している場合、クラス A には、クラス B を保持するプロセス外の COM サーバーと通信するプロキシ オブジェクトが必要になります。サーバーがメモリ不足になってもクラス A が認識しないことがあります。 この場合、例外 RPC_E_DISCONNECTED はスローされ、Platform::DisconnectedException に変換されます。 これが発生する 1 つのシナリオは、イベント ソースに渡されたデリゲートをイベント ソースが呼び出したものの、イベントをサブスクライブした後のある時点でデリゲートが破棄された場合です。 この場合、イベント ソースは、呼び出しリストからそのデリゲートを削除します。

詳細については、 [COMException](../cppcx/platform-comexception-class.md) クラスを参照してください。

### <a name="requirements"></a>必要条件

**最小値には、クライアントがサポートされています。** Windows 8

**最小値には、サーバーがサポートされています。** Windows Server 2012

**名前空間:** プラットフォーム

**メタデータ:** platform.winmd

## <a name="see-also"></a>関連項目

[Platform::COMException クラス](../cppcx/platform-comexception-class.md)
