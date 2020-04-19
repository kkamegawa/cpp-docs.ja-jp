---
title: HSE_VERSION_INFO 構造体
ms.date: 11/04/2016
f1_keywords:
- HSE_VERSION_INFO
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
ms.openlocfilehash: 97f34bebae8a486a825d04b23c5a92fbd4aefa42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322115"
---
# <a name="hseversioninfo-structure"></a>HSE_VERSION_INFO 構造体

この構造体を指す、 *pVer*パラメーター、`CHttpServer::GetExtensionVersion`メンバー関数。 ISA のバージョン番号と、ISA の説明テキストを提供します

## <a name="syntax"></a>構文

```
typedef struct _HSE_VERSION_INFO {
    DWORD dwExtensionVersion;
    CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;
```

#### <a name="parameters"></a>パラメーター

*dwExtensionVersion*<br/>
ISA のバージョン番号

*lpszExtensionDesc*<br/>
ISA のテキストの説明 既定の実装は、プレース ホルダー テキストを提供します。オーバーライド`CHttpServer::GetExtensionVersion`を独自の説明を提供します。

## <a name="requirements"></a>必要条件

**ヘッダー:** httpext.h

## <a name="see-also"></a>関連項目

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
