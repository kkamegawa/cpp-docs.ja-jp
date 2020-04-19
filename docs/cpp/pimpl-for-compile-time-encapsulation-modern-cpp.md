---
title: コンパイル時のカプセル化の Pimpl (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
ms.openlocfilehash: f1eb06ad3a52be486f085babf699677951b1ee71
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245175"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>コンパイル時のカプセル化の Pimpl (Modern C++)

*Pimpl*表現は、実装をC++非表示にするための最新の手法であり、結合を最小限にし、インターフェイスを分離します。 Pimpl は、"実装へのポインター" の省略形です。 概念は既に理解しているものの、Cheshire Cat や Compiler Firewall イディオムなどの他の名前で理解している場合があります。

## <a name="why-use-pimpl"></a>Pimpl を使用する理由

次に、pimpl 表現を使用してソフトウェア開発ライフサイクルを改善する方法を示します。

- コンパイル依存関係の最小化。

- インターフェイスと実装の分離。

- 携帯.

## <a name="pimpl-header"></a>Pimpl ヘッダー

```cpp
// my_class.h
class my_class {
   //  ... all public and protected stuff goes here ...
private:
   class impl; unique_ptr<impl> pimpl; // opaque type here
};
```

Pimpl 表現は、カスケードおよび不安定なオブジェクトレイアウトの再構築を回避します。 (推移的な) 人気のある型に適しています。

## <a name="pimpl-implementation"></a>Pimpl 実装

.Cpp ファイルで `impl` クラスを定義します。

```cpp
// my_class.cpp
class my_class::impl {  // defined privately here
  // ... all private data and functions: all of these
  //     can now change without recompiling callers ...
};
my_class::my_class(): pimpl( new impl )
{
  // ... set impl values ...
}
```

## <a name="best-practices"></a>ベスト プラクティス

スローしないスワップ特殊化のサポートを追加するかどうかを検討します。

## <a name="see-also"></a>参照

[に戻るC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[C++ 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)
