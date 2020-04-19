---
title: コンテナー クラス::erase
ms.date: 11/04/2016
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
ms.openlocfilehash: 1fa3fe7dee10f3033b84a671fdc35c193cd6ec3c
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257898"
---
# <a name="container-classerase"></a>コンテナー クラス::erase

> [!NOTE]
> このトピックは、 C++ C++標準ライブラリで使用されているコンテナーの非機能例として、Microsoft ドキュメントに記載されています。 詳しくは、「[C++ 標準ライブラリのコンテナー](../standard-library/stl-containers.md)」をご覧ください。

要素を消去します。

## <a name="syntax"></a>構文

```cpp
iterator erase(
    iterator _Where);

iterator erase(
    iterator first,
    iterator last);
```

## <a name="remarks"></a>コメント

1つ目のメンバー関数は、 *_Where*が指す被制御シーケンスの要素を削除します。 2 番目のメンバー関数は、範囲 [`first`, `last`) の被制御シーケンスの要素を削除します。 どちらも、削除した要素の後に残る最初の要素を指定する反復子を返します。そのような要素が存在しない場合は、[end](../standard-library/container-class-end.md) を返します。

メンバー関数は、コピー操作が例外をスローする場合にのみ、例外をスローします。

## <a name="see-also"></a>参照

[サンプル コンテナー クラス](../standard-library/sample-container-class.md)
