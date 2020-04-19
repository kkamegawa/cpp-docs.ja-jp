---
title: コンパイラ エラー C3445
ms.date: 04/10/2017
f1_keywords:
- C3445
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
ms.openlocfilehash: 2eddeb5a56c953ca0864e29187fbe28c53bdee24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328654"
---
# <a name="compiler-error-c3445"></a>コンパイラ エラー C3445

> コピーのリストの初期化の '*型*' 明示的なコンス トラクターを使用することはできません

ISO C 17 標準に従って、コンパイラは、コピー リストの初期化でオーバー ロードの解決の明示的なコンス トラクターを考慮する必要が、そのオーバー ロードを実際に選択した場合、エラーが発生する必要があります。

Visual Studio 2017 以降、コンパイラは、Visual Studio 2015 で見つからなかった、初期化子リストを使用してオブジェクトの作成に関連するエラーを検索します。 これらのエラーは、クラッシュまたは実行時に未定義の動作をする可能性があります。

## <a name="example"></a>例

次の例では、C3445 が生成されます。

```cpp
// C3445.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of
                      //     'A' cannot use an explicit constructor
}
```

エラーを修正するには、直接の初期化を代わりに使用します。

```cpp
// C3445b.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1{ 1 };
}
```
