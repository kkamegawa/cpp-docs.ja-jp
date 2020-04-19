---
title: /ALLOWBIND
ms.date: 11/04/2016
f1_keywords:
- /allowbind
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
ms.openlocfilehash: 4cb7e5a3627d865e2f2193dee096c72cced75f5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273197"
---
# <a name="allowbind"></a>/ALLOWBIND

DLL をバインドできるかどうかを指定します。

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Remarks

**/ALLOWBIND**オプションは、ビット イメージがバインドできることを Bind.exe に指示を示します DLL のヘッダーを設定します。 バインディングは、高速に読み込むリベースを各参照されている DLL をアドレスのフィックス アップを実行する、ローダーがない場合にイメージを許可できます。 デジタル署名されている場合にバインドする DLL は避けたい-バインドには、署名が無効になります。 バインディングには効果がないを使用して、イメージのアドレス空間レイアウト randomization (ASLR) が有効になっている場合 **/DYNAMICBASE** ASLR をサポートする Windows のバージョン。

使用 **/ALLOWBIND:NO** Bind.exe が DLL をバインドするを防ぐためにします。

詳細については、次を参照してください。、 [/ALLOWBIND](allowbind-prevent-dll-binding.md)リンカー オプション。

## <a name="see-also"></a>関連項目

[EDITBIN オプション](editbin-options.md)
