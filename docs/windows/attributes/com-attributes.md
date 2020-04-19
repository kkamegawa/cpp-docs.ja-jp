---
title: COM 属性
ms.date: 10/03/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
ms.openlocfilehash: eb87d3861c6b3066cf482108e2ce2243c8196093
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148472"
---
# <a name="com-attributes"></a>COM 属性

COM 属性は、COM の開発と .NET Framework 共通言語ランタイムによる開発のさまざまな領域をサポートするためにコードを挿入します。 領域はこれらカスタム インターフェイスの実装と既存のインターフェイスのサポートからストック プロパティ、メソッド、およびイベントをサポートする範囲。 さらに、複合デバイスと ActiveX コントロールの実装のサポートを確認できます。

|属性|説明|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|別のコントロールでコントロールを集計できることを示します。|
|[aggregates](aggregates.md)|コントロールがターゲット クラスを集約することを示します。|
|[coclass](coclass.md)|COM インターフェイスを実装できる COM オブジェクトを作成します。|
|[com_interface_entry](com-interface-entry-cpp.md)|COM マップには、インターフェイスのエントリを追加します。|
|[implements_category](implements-category.md)|クラスの実装されたコンポーネントのカテゴリを指定します。|
|[progid](progid.md)|コントロールの ProgID を定義します。|
|[rdx](rdx.md)|作成またはレジストリ キーを変更します。|
|[registration_script](registration-script.md)|指定した登録スクリプトを実行します。|
|[requires_category](requires-category.md)|クラスの必須コンポーネントのカテゴリを指定します。|
|[support_error_info](support-error-info.md)|ターゲット オブジェクトのエラー報告をサポートしています。|
|[synchronize](synchronize.md)|メソッドへのアクセスを同期します。|
|[threading](threading-cpp.md)|COM オブジェクトのスレッド モデルを指定します。|
|[vi_progid](vi-progid.md)|コントロールのバージョンに依存しないプログラム Id を定義します。|

## <a name="see-also"></a>関連項目

[グループ別の属性](attributes-by-group.md)