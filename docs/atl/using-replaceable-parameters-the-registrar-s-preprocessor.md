---
title: 置き換え可能パラメーター (ATL レジストラー) を使用します。
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: 1c772c0493b351d8452400a4fb1e3949ab6f28f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274145"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>置き換え可能パラメーターを使用して (レジストラー&#39;s プリプロセッサ)

置き換え可能パラメーターを使用すると、レジストラーのクライアントで実行時のデータを指定します。 これを行うには、レジストラーは、先が、スクリプトで置き換え可能パラメーターに関連付けられている値に入る置換マップを保持します。 レジストラーは、実行時にこれらのエントリを作成します。

##  <a name="_atl_using_.25.module.25"></a> % モジュールを使用します。

[ATL コントロール ウィザード](../atl/reference/atl-control-wizard.md)を使用するスクリプトを自動的に生成`%MODULE%`します。 ATL は、サーバーの DLL または EXE の実際の場所をこの置き換え可能パラメーターを使用します。

## <a name="concatenating-run-time-data-with-script-data"></a>実行時データとスクリプトのデータを連結します。

プリプロセッサの別の使用では、実行時データとスクリプトのデータを連結します。 たとえば、エントリが必要な文字列を持つモジュールへの完全パスを含む"`, 1`"最後に追加します。 まず、次の拡張を定義します。

```
'MySampleKey' = s '%MODULE%, 1'
```

次に、前に呼び出すメソッドの一覧を処理するスクリプトのいずれかの[スクリプトの呼び出し](../atl/invoking-scripts.md)マップの代わりに追加。

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

スクリプトの解析中に、レジストラーが展開`'%MODULE%, 1'`に`c:\mycode\mydll.dll, 1`します。

> [!NOTE]
>  レジストラー スクリプトでは、4 K は、最大トークン サイズです。 (トークンは、構文内の認識可能な要素です)。これには、作成またはプリプロセッサによって展開されたトークンが含まれます。

> [!NOTE]
>  実行時に置換値を置換するに、スクリプト内の呼び出しを削除、[に](../atl/reference/registry-macros.md#declare_registry_resource)または[代入](../atl/reference/registry-macros.md#declare_registry_resourceid)マクロ。 代わりに、独自に置き換えます`UpdateRegistry`メソッドを呼び出す[として](../atl/reference/catlmodule-class.md#updateregistryfromresourced)または[方法については](../atl/reference/catlmodule-class.md#updateregistryfromresources)_ATL_REGMAP_ の配列を渡すエントリの構造体。 _ATL_REGMAP_ENTRY の配列には、{NULL、NULL} に設定されている少なくとも 1 つのエントリが必要し、このエントリが最後のエントリには常にします。 それ以外の場合、アクセス違反エラーになる時に生成される`UpdateRegistryFromResource`が呼び出されます。

> [!NOTE]
>  ATL が自動的に実行時に作成されたパス名を囲む引用符を追加実行可能ファイルを出力するプロジェクトを作成するときに、 **% モジュール**レジストラー スクリプトのパラメーター。 パス名に引用符を含めるしたくない場合は、新しい使用 **%module_raw**パラメーター代わりにします。
>
>  DLL を出力するプロジェクトを作成するときに場合は、ATL が引用符をパス名は追加することはしません **% モジュール**または **%module_raw**使用されます。

## <a name="see-also"></a>関連項目

[レジストラー スクリプトの作成](../atl/creating-registrar-scripts.md)
