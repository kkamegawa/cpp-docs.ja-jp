---
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: 59ada8a7e098e57cca5641a439365851bbae2485
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155073"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo

**Microsoft 固有の仕様**

コンストラクターに渡された `IErrorInfo` オブジェクトを取得します。

## <a name="syntax"></a>構文

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>戻り値

コンストラクターに渡された未処理の `IErrorInfo` 項目。

## <a name="remarks"></a>Remarks

カプセル化された取得`IErrorInfo`内の項目を`_com_error`オブジェクト、または、ない場合は NULL`IErrorInfo`項目が記録されます。 呼び出し元が呼び出す必要があります`Release`完了すると、返されたオブジェクトを使用します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_error クラス](../cpp/com-error-class.md)