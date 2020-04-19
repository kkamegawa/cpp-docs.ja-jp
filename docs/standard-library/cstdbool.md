---
title: '&lt;cstdbool&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdbool>
- cstdbool
helpviewer_keywords:
- cstdbool header
ms.assetid: 44ccb8b2-d808-4715-8097-58ba09ab33ed
ms.openlocfilehash: ed780e059a5e456731fd6a4f651639e282016f5e
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341104"
---
# <a name="ltcstdboolgt"></a>&lt;cstdbool&gt;

C 標準ライブラリヘッダー \<stdbool. > をインクルードし、関連`std`する名前を名前空間に追加します。

> [!NOTE]
> > Stdbool. ヘッダーでは、のキーワードでC++あるマクロが定義されているため、これを含めても効果はありません。 \< Stdbool. \<> ヘッダーは、でC++は非推奨とされます。 \<Cstdbool > ヘッダーは c++ 17 では非推奨とされており、draft c++ 20 standard では削除されています。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<cstdbool >

**名前空間:** std

## <a name="remarks"></a>Remarks

このヘッダーをインクルードすると、C 標準ライブラリヘッダーの外部リンケージを使用して宣言され`std`た名前が、名前空間で宣言されます。

## <a name="see-also"></a>関連項目

[ヘッダーファイルのリファレンス](cpp-standard-library-header-files.md)\
[C++標準ライブラリの概要](cpp-standard-library-overview.md)\
[C++標準ライブラリのスレッドセーフ](thread-safety-in-the-cpp-standard-library.md)
