---
title: 名前の装飾
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: d1557f53a07a544ff4f9e5a63f905e6854fb74ce
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857166"
---
# <a name="name-decoration"></a>名前の装飾

名前の装飾は、通常は C++ の名前付け規則を指しますが、C の場合でもよく適用されます。 既定では、C++ では関数名、パラメーター、および戻り値の型を使用して、関数のリンカー名が作成されます。 次の関数宣言を検討してください。

`void CALLTYPE test(void);`

次の表は、さまざまな呼び出し規約のリンカー名を示します。

|呼び出し規則|`extern "C"` または`.c`ファイル|`.cpp`、`.cxx`または `/TP`|
|------------------------|---------------------------|------------------------|
|C の名前付け規則 (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|高速呼び出しの名前付け規則 (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|標準呼び出しの名前付け規則 (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|ベクターの呼び出しの名前付け規則 (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

使用`extern "C"`から C 関数を呼び出すC++します。 `extern "C"` クラス以外の C の名前付け規則の使用を強制C++関数。 コンパイラ スイッチに注意してください。 **/Tc**または **/Tp**、コンパイラがファイル名拡張子を無視して、ファイルをそれぞれ C または C++ としてコンパイルするように指示します。 これらのオプションと思わないリンカー名があります。

関数プロトタイプのパラメーターが一致していないと、このエラーが発生します。 名前の装飾では、関数のパラメーターを最終の装飾関数名に組み込みます。 関数宣言と一致しないパラメーターの型と関数を呼び出すと、LNK2001 場合もあります。

現在の標準はありませんC++コンパイラ ベンダー間またはコンパイラの異なるバージョン間であっても名前を付けます。 別のコンパイラでコンパイルされたオブジェクト ファイルをリンクして、同一の名前付けスキームにならない可能性がある、未解決の外部参照が発生することができます。

## <a name="see-also"></a>関連項目

[リンカー ツール エラー LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)