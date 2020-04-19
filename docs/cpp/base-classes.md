---
title: 基本クラス
ms.date: 11/19/2018
helpviewer_keywords:
- inheritance, multiple
- base classes [C++], virtual
- derived classes [C++], multiple bases
- multiple inheritance, base classes
- virtual base classes [C++]
- base classes [C++]
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
ms.openlocfilehash: 59c474f54ea439acf83cf6923eba6e167901dd37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392420"
---
# <a name="base-classes"></a>基本クラス

継承プロセスは、基底クラス、および派生クラスによって追加された新しいメンバーで構成される、新しい派生クラスを作成します。 多重継承では、同じ基底クラスが複数の派生クラスの一部になる継承グラフが生成される場合があります。 次の図は、こうしたグラフを示しています。

![基底クラスの複数のインスタンス](../cpp/media/vc38xn1.gif "基底クラスの複数のインスタンス") <br/>
1 つの基本クラスの複数のインスタンス

図では、`CollectibleString` と `CollectibleSortable` のコンポーネントのイメージ表現が表示されます。 ただし、基底クラス `Collectible` は、`CollectibleSortableString` パスと `CollectibleString` パスを経由した `CollectibleSortable` 内にあります。 この冗長性を取り除くために、継承されるときにこのようなクラスを仮想基底クラスとして宣言できます。