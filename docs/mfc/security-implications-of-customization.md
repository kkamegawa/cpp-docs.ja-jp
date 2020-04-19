---
title: カスタマイズによるセキュリティへの影響
ms.date: 11/04/2016
helpviewer_keywords:
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
ms.openlocfilehash: 9164983a6634e069195f3498bea56b595a2a2381
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308473"
---
# <a name="security-implications-of-customization"></a>カスタマイズによるセキュリティへの影響

このトピックでは、MFC での潜在的なセキュリティ脆弱性について説明します。

## <a name="potential-security-weakness"></a>潜在的なセキュリティの脆弱性

MFC で、ユーザーは、ボタンとアイコンの外観など、アプリケーション ユーザー インターフェイスの外観をカスタマイズします。 MFC には、シェル コマンドを実行できるユーザー定義のツールもサポートしています。 アプリケーションのカスタマイズした設定はレジストリ内のユーザー プロファイルに保存されるため、セキュリティの脆弱性が発生します。 これらの設定を編集し、アプリケーションの外観や動作を変更、レジストリにアクセスできるユーザーはだれでもできます。 など、コンピューターの管理者では、(ネットワーク共有) からでも任意のプログラムを実行するユーザーのアプリケーションを発生させることによってユーザーを偽装する可能性があります。

## <a name="workarounds"></a>問題回避

レジストリの脆弱性を終了するこれら 3 つの方法のいずれかをお勧めします。

- 保管されているデータを暗号化します。

- レジストリではなく、セキュリティで保護されたファイルにデータを格納します。

   これらの最初の 2 つの方法のいずれかを行うためには、派生クラスを[CSettingsStore クラス](../mfc/reference/csettingsstore-class.md)し、暗号化またはレジストリ以外で記憶域を実装するメソッドをオーバーライドします。

- また、アプリケーションでカスタマイズを無効にします。

## <a name="see-also"></a>関連項目

[MFC のカスタマイズ](../mfc/customization-for-mfc.md)
