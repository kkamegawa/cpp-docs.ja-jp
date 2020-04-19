---
title: Visual C++ 6.0 以降の DLL 遅延読み込みヘルパー関数の変更点
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
ms.openlocfilehash: cd6e842fd6d35e05f2d5a9f906713f0d85d3b80d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294630"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Visual C++ 6.0 以降の DLL 遅延読み込みヘルパー関数の変更点

コンピューターに複数のバージョンの Visual C があるか、独自のヘルパー関数を定義する場合を受ける可能性がありますには、DLL に加えられた変更が遅延読み込みヘルパー関数。 例えば:

- **_ _delayloadhelper**が **_ _delayloadhelper2**

- **__pfnDliNotifyHook**が **__pfnDliNotifyHook2**

- **__pfnDliFailureHook**が **__pfnDliFailureHook2**

- **__FUnloadDelayLoadedDLL**が **__FUnloadDelayLoadedDLL2**

> [!NOTE]
>  既定のヘルパー関数を使用している場合は、これらの変更は影響を与えません。 リンカーを呼び出す方法に関する変更はありません。

## <a name="multiple-versions-of-visual-c"></a>複数のバージョンの Visual C

コンピューターに複数のバージョンの Visual C をした場合、リンカーは、delayimp.lib と一致することを確認します。 いずれかを報告リンカー エラーが発生した不一致がある場合は`___delayLoadHelper2@8`または`___delayLoadHelper@8`未解決の外部シンボルとして。 前者を古い delayimp.lib では、新しいリンカーを意味し、後者の場合、古いリンカーを新しい delayimp.lib を意味します。

未解決のリンカー エラーが発生する場合は、実行[dumpbin/linkermember](linkermember.md): 1 にするヘルパー関数が代わりに定義されているヘルパー関数を含める必要のある delayimp.lib にします。 ヘルパー関数は、オブジェクト ファイルで定義することも可能性があります。実行[dumpbin/symbols](symbols.md)を探して`delayLoadHelper(2)`します。

わかっている場合、Visual C 6.0 リンカーが、あります。

- 遅延読み込みヘルパーの .lib ファイルや .obj ファイルを定義するかどうかを判断する上での dumpbin の実行 **_ _delayloadhelper2**します。 それ以外の場合は、リンクは失敗します。

- 定義 **_ _delayloadhelper**遅延読み込みヘルパーの .lib または .obj ファイル。

## <a name="user-defined-helper-function"></a>ユーザー定義のヘルパー関数

独自のヘルパー関数を定義し、現在のバージョンの Visual C を使用している場合は、次の操作を行います。

- ヘルパー関数の名前を変更 **_ _delayloadhelper2**します。

- 遅延記述子 (delayimp.h で ImgDelayDescr) でポインターは、絶対アドレス (VAs) から相対アドレス (Rva) 32 ビットおよび 64 ビットの両方のプログラムに正常に動作に変更されましたが、ために、これらをポインターに変換する必要があります。 新しい関数が導入されています。PFromRva、delayhlp.cpp で見つかりました。 それぞれの記述子フィールドのこの関数を使用すると、それらをいずれかの 32 ビットまたは 64 ビット ポインターに変換します。 既定の遅延読み込みヘルパー関数は、例として使用する適切なテンプレートです。

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>遅延読み込み DLL のすべてのインポートを読み込む

リンカーは、遅延読み込みをするように指定した DLL からのすべてのインポートを読み込むことができます。 参照してください[すべてのインポートを「読み込み](loading-all-imports-for-a-delay-loaded-dll.md)詳細についてはします。

## <a name="see-also"></a>関連項目

[ヘルパー関数について](understanding-the-helper-function.md)
