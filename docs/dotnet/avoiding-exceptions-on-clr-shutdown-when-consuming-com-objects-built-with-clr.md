---
title: -Clr で構築された COM オブジェクトによってスローされた例外を回避します。
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
ms.openlocfilehash: bafcfb4e8a8abfecc8491220202b63971bef1ac8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393832"
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>/clr で構築された COM オブジェクト使用時における CLR シャットダウンの例外の回避

シャット ダウン モードに入ると、共通言語ランタイム (CLR) とネイティブ関数には、CLR サービスへのアクセスが制限されます。 COM オブジェクトをコンパイルした Release を呼び出すしようとしています。 **/clr**、ネイティブ コードに CLR が遷移と遷移 (マネージ コードで定義) される:release 呼び出しに対応するマネージ コードに戻さします。 シャット ダウン モードにあるために、CLR はマネージ コードへのコールバックを防ぎます。

これを解決するには、リリース メソッドから呼び出されるデストラクターがネイティブ コードだけを格納することを確認します。

## <a name="see-also"></a>関連項目

[混在 (ネイティブおよびマネージド) アセンブリ](../dotnet/mixed-native-and-managed-assemblies.md)
