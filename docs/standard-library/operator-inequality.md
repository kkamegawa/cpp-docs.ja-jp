---
title: operator!=
ms.date: 11/04/2016
f1_keywords:
- std::!=
- '!='
- std::operator!=
- std.operator!=
- std.!=
- operator!=
helpviewer_keywords:
- '!= operator'
- operator!=
- operator !=
ms.assetid: ef2be7f0-1c94-4edc-b65c-731fddd519f4
ms.openlocfilehash: 89d41d099d151f77d91cd94b22047824779dcf54
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687345"
---
# <a name="operator"></a>operator!=

> [!NOTE]
> このトピックは、 C++ C++標準ライブラリで使用されているコンテナーの非機能例として、Microsoft ドキュメントに記載されています。 詳細については、「[C++ Standard Library Containers (C++ 標準ライブラリ コンテナ―)](../standard-library/stl-containers.md)」をご覧ください。

オーバーロード `operator!=` クラステンプレート[コンテナー](../standard-library/sample-container-class.md)の2つのオブジェクトを比較します。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
bool operator!=(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>戻り値

`!(left == right)`を返します。

## <a name="see-also"></a>関連項目

[\<sample container>](../standard-library/sample-container.md)
