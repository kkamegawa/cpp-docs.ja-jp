---
title: future_error クラス
ms.date: 11/04/2016
f1_keywords:
- future/std::future_error
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
ms.openlocfilehash: ed3f9d63c45d0e185e3e1476094736d132822173
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447348"
---
# <a name="futureerror-class"></a>future_error クラス

[future](../standard-library/future-class.md) オブジェクトを管理する型のメソッドによってスローされる例外オブジェクトを記述します。

## <a name="syntax"></a>構文

```cpp
class future_error : public logic_error {
public:
    future_error(error_code code);

const error_code& code() const throw();

const char *what() const throw();

};
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<今後の >

**名前空間:** std

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[logic_error クラス](../standard-library/logic-error-class.md)\
[error_code クラス](../standard-library/error-code-class.md)
