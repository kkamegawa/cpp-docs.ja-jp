---
title: system_error クラス
ms.date: 11/04/2016
f1_keywords:
- system_error/std::system_error
helpviewer_keywords:
- system_error class
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
ms.openlocfilehash: 3f544cac1835a5a01e4d287cee1084bc56141716
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246240"
---
# <a name="systemerror-class"></a>system_error クラス

低レベル システムエラーをレポートするためにスローされるすべての例外のための基底クラスを表します。

## <a name="syntax"></a>構文

```cpp
class system_error : public runtime_error {
    explicit system_error(error_code _Errcode, const string& _Message = "");
    system_error(error_code _Errcode, const char *_Message);
    system_error(error_code::value_type _Errval, const error_category& _Errcat, const string& _Message);
    system_error(error_code::value_type _Errval, const error_category& _Errcat, const char *_Message);
    
    const error_code& code() const throw();
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Remarks

クラス [exception](../standard-library/exception-class.md) で `what` によって返される値は、`_Message` および型 [error_code](../standard-library/error-code-class.md) (`code` または `error_code(_Errval, _Errcat)` のいずれか) の格納されているオブジェクトから構築されます。

メンバー関数 `code` は、格納されている [error_code](../standard-library/error-code-class.md) オブジェクトを返します。
