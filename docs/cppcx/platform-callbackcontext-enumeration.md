---
title: Platform::CallbackContext 列挙型
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
ms.openlocfilehash: 7f4e020ab0b1e377456c27d3b4666e15b5a4f7a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161681"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext 列挙型

コールバック関数 (イベント ハンドラー) が実行するスレッド コンテキストを指定します。

## <a name="syntax"></a>構文

```cpp
enum class CallbackContext {};
```

### <a name="members"></a>メンバー

|型コード|説明|
|---------------|-----------------|
|どれでも可|コールバック関数は、任意のスレッド コンテキストで実行できます。|
|同|コールバック関数は、非同期操作を開始したスレッド コンテキストでのみ実行できます。|

### <a name="requirements"></a>必要条件

**最小値には、クライアントがサポートされています。** Windows 8

**最小値には、サーバーがサポートされています。** Windows Server 2012

**名前空間:** プラットフォーム

**メタデータ:** platform.winmd