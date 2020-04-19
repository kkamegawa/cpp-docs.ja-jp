---
title: AsyncStatusInternal 列挙型
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: f12bf4aafc87e44a6e2fb15ba79de4a9744bea58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398785"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal 列挙型

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
enum AsyncStatusInternal;
```

## <a name="remarks"></a>Remarks

非同期操作の状態の内部列挙値の間のマッピングを指定します、`Windows::Foundation::AsyncStatus`列挙体。

## <a name="members"></a>メンバー

`_Created`<br/>
`::Windows::Foundation::AsyncStatus::Created` と同じ意味です。

`_Started`<br/>
`::Windows::Foundation::AsyncStatus::Started` と同じ意味です。

`_Completed`<br/>
`::Windows::Foundation::AsyncStatus::Completed` と同じ意味です。

`_Cancelled`<br/>
`::Windows::Foundation::AsyncStatus::Cancelled` と同じ意味です。

`_Error`<br/>
`::Windows::Foundation::AsyncStatus::Error` と同じ意味です。

## <a name="requirements"></a>必要条件

**ヘッダー:** async.h

**名前空間:** Microsoft::WRL::Details

## <a name="see-also"></a>関連項目

[Microsoft::WRL::Details 名前空間](microsoft-wrl-details-namespace.md)