---
title: '方法: Registration-free COM コンポーネントを構築します。'
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 783677c97835acc98751fc4a19f9405af752b71a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188939"
---
# <a name="how-to-build-registration-free-com-components"></a>方法: Registration-free COM コンポーネントを構築します。

登録を必要としない COM コンポーネントは、Dll に組み込まれているマニフェストのある COM コンポーネントです。

### <a name="to-build-manifests-into-com-components"></a>COM コンポーネントにマニフェストをビルドするには

1. COM コンポーネントのプロジェクト プロパティ ページを開きます。

1. 展開、**構成プロパティ**ノードの順に展開し、**マニフェスト ツール**ノード。

1. 選択、**入力し、出力**プロパティ ページ、および設定して、**埋め込みマニフェスト**プロパティを等しく**はい**します。

1. **[OK]** をクリックします。

1. ソリューションをビルドします。

## <a name="see-also"></a>関連項目

[方法: COM コンポーネントを使用する分離アプリケーションをビルドする](how-to-build-isolated-applications-to-consume-com-components.md)
