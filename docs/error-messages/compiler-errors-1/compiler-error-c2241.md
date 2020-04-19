---
title: コンパイラ エラー C2241
ms.date: 11/04/2016
f1_keywords:
- C2241
helpviewer_keywords:
- C2241
ms.assetid: 2f4e2c2c-b95c-4afe-bbe0-4214cd39d140
ms.openlocfilehash: 88f25931d84fe3884ebecbc97b9ddd73390bacc2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388970"
---
# <a name="compiler-error-c2241"></a>コンパイラ エラー C2241

'identifier' : メンバー アクセスは制限されています

コードが、プライベート メンバーまたはプロテクト メンバーにアクセスしようとしています。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>以下の可能性がある解決策を使って修正するには

1. メンバーのアクセス レベルを変更します。

1. アクセスする関数の `friend` としてメンバーを宣言します。