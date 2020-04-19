---
title: /INTEGRITYCHECK
ms.date: 12/28/2017
f1_keywords:
- /INTEGRITYCHECK
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.openlocfilehash: 4174e22dcdadb3b3319998614285c13741fe3a88
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269766"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

読み込み時にバイナリ イメージのデジタル署名を確認する必要があることを指定します。

> **/INTEGRITYCHECK** **[:NO]**

## <a name="remarks"></a>Remarks

DLL ファイルまたは実行可能ファイルのヘッダーで、このオプションは、Windows でイメージを読み込むために、メモリ マネージャーによるデジタル署名の確認を必要とするフラグを設定します。 Windows Vista 以前の Windows は、このフラグを無視します。 このオプションは、カーネル モード コードを実装する 64 ビット DLL には設定する必要があり、またすべてのデバイス ドライバーに推奨されます。 詳細については、次を参照してください。[カーネル モード コード署名要件](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)します。

## <a name="see-also"></a>関連項目

[EDITBIN オプション](editbin-options.md)
