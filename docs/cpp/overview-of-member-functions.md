---
title: メンバー関数の概要
ms.date: 11/04/2016
helpviewer_keywords:
- this pointer, and nonstatic member functions
- nonstatic member functions [C++]
- inline functions [C++], treating member functions as
- member functions [C++], definition in class declaration
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
ms.openlocfilehash: faa7d016c8f48e9a5ee57c8efa4ce3dfd3f3eb01
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345853"
---
# <a name="overview-of-member-functions"></a>メンバー関数の概要

メンバー関数は静的か非静的のいずれかになります。 静的メンバー関数の動作は、静的メンバー関数は暗黙ために、他のメンバー関数とは異なります。**this**引数。 非静的メンバー関数が、**this**ポインター。 メンバー関数は、静的であるないにかかわらず、クラス宣言の内外に定義できます。

メンバー関数がクラス宣言の中で定義されている場合、インライン関数として扱われ、そのクラス名で関数名を修飾する必要はありません。 使用することができますが、クラス宣言内で定義されている関数がインライン関数として扱われますが、**inline**コードを説明するキーワード。

クラス宣言内で関数を宣言する例を示します。

```cpp
// overview_of_member_functions1.cpp
class Account
{
public:
    // Declare the member function Deposit within the declaration
    //  of class Account.
    double Deposit( double HowMuch )
    {
        balance += HowMuch;
        return balance;
    }
private:
    double balance;
};

int main()
{
}
```

として明示的に宣言されている場合にのみ、メンバー関数の定義がクラス宣言の外側にある場合には、インライン関数として扱わ**inline**します。 また、定義内の関数名はスコープ解決演算子 (`::`) を使用してクラス名で修飾する必要があります。

次の例は、`Account` 関数がクラス宣言の外側で定義されていることを除き、クラス `Deposit` の以前の宣言と同じです。

```cpp
// overview_of_member_functions2.cpp
class Account
{
public:
    // Declare the member function Deposit but do not define it.
    double Deposit( double HowMuch );
private:
    double balance;
};

inline double Account::Deposit( double HowMuch )
{
    balance += HowMuch;
    return balance;
}

int main()
{
}
```

> [!NOTE]
>  メンバー関数がクラス宣言の内部でも個別でも定義できますが、メンバー関数は、クラスが定義された後でクラスに追加することはできません。

メンバー関数を含むクラスは多くの宣言を持つことができますが、メンバー関数自体は 1 つのプログラムに定義を 1 つのみ持つ必要があります。 複数の定義により、リンク時にエラー メッセージが発生します。 クラスにインライン関数定義が含まれている場合、この "1 つの定義" 規則に従うために、関数定義は同じにする必要があります。