---
title: LIBRARY
ms.date: 11/04/2016
f1_keywords:
- LIBRARY
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
ms.openlocfilehash: b43f269726e8925abeefd41aab0edfd57b071035
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291094"
---
# <a name="library"></a>LIBRARY

DLL を作成するリンクを示します。 同時に、リンクは、ビルドで .exp ファイルを使用しない場合、インポート ライブラリを作成します。

```
LIBRARY [library][BASE=address]
```

## <a name="remarks"></a>Remarks

*ライブラリ*引数が DLL の名前を指定します。 使用することも、 [/out](out-output-file-name.md) DLL の出力名を指定するリンカー オプション。

ベース =*アドレス*引数は、オペレーティング システムが DLL の読み込みに使用するベース アドレスを設定します。 この引数は、0x10000000 の既定の DLL の場所を上書きします。 説明を参照して、 [/base](base-base-address.md)オプションの詳細については、ベース アドレス。

使用してください、 [/DLL](dll-build-a-dll.md) DLL をビルドするときに、リンカー オプション。

## <a name="see-also"></a>関連項目

[モジュール定義ステートメントに関する規則](rules-for-module-definition-statements.md)
