---
title: 正規表現 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- regular expressions [C++]
- .NET Framework [C++], regular expressions
- regular expressions [C++], about regular expressions
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- Split method, parsing strings
- strings [C++], parsing
- substrings, simple matches
- searching, exact substring matches
- strings [C++], exact substring matching
- regular expressions [C++], simple matching
- IsMatch method
- strings [C++], extracting data from
- formatted strings [C++]
- regular expressions [C++], extracting data fields
- data [C++], extracting from strings
- regular expressions [C++], rearranging data
- data [C++], rearranging
- search and replace
- Replace method
- regular expressions [C++], search and replace
- strings [C++], formatting
- data [C++], formatting
- regular expressions [C++], validating data formatting
ms.assetid: 838bab49-0dbc-4089-a604-ef146269ef5a
ms.openlocfilehash: 24a278e4d5b208c5d8e3b95b9f5a0bd0306dbab3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384663"
---
# <a name="regular-expressions-ccli"></a>正規表現 (C++/CLI)

.NET Framework の正規表現クラスを使用して、さまざまな文字列操作を示します。

次のトピックでは、.NET Framework の使用<xref:System.Text.RegularExpressions>名前空間 (1 つの場合、<xref:System.String.Split%2A?displayProperty=fullName>メソッド) を検索するには、解析、および文字列を変更します。

## <a name="parse_regex"></a> 正規表現を使用して文字列を解析します。

<xref:System.Text.RegularExpressions.Regex> 名前空間の <xref:System.Text.RegularExpressions?displayProperty=fullName> クラスを使用して単純な文字列を解析する方法を次のコード例に示します。 複数のワード デリニエイタの型を含む文字列が構成されます。 次に、<xref:System.Text.RegularExpressions.Regex> クラスを <xref:System.Text.RegularExpressions.Match> クラスと共に使用して文字列が解析されます。 さらに、センテンス内の各単語を個別に表示します。

### <a name="example"></a>例

```cpp
// regex_parse.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main( )
{
   int words = 0;
   String^ pattern = "[a-zA-Z]*";
   Console::WriteLine( "pattern : '{0}'", pattern );
   Regex^ regex = gcnew Regex( pattern );

   String^ line = "one\ttwo three:four,five six  seven";
   Console::WriteLine( "text : '{0}'", line );
   for( Match^ match = regex->Match( line );
        match->Success; match = match->NextMatch( ) )
   {
      if( match->Value->Length > 0 )
      {
         words++;
         Console::WriteLine( "{0}", match->Value );
      }
   }
   Console::WriteLine( "Number of Words : {0}", words );

   return 0;
}
```

## <a name="parse_split"></a> Split メソッドを使用して文字列を解析します。

<xref:System.String.Split%2A?displayProperty=fullName> メソッドを使用して、文字列から各単語を抽出する方法を次のコード例に示します。 デリニエイタ リストを指定して <xref:System.String.Split%2A> を呼び出すと、複数の型のワード デリニエイタを含む文字列が構成され、解析されます。 さらに、センテンス内の各単語を個別に表示します。

### <a name="example"></a>例

```cpp
// regex_split.cpp
// compile with: /clr
using namespace System;

int main()
{
   String^ delimStr = " ,.:\t";
   Console::WriteLine( "delimiter : '{0}'", delimStr );
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ words;
   String^ line = "one\ttwo three:four,five six seven";

   Console::WriteLine( "text : '{0}'", line );
   words = line->Split( delimiter );
   Console::WriteLine( "Number of Words : {0}", words->Length );
   for (int word=0; word<words->Length; word++)
      Console::WriteLine( "{0}", words[word] );

   return 0;
}
```

## <a name="regex_simple"></a> 単純なマッチングに正規表現を使用します。

次のコード例では、正規表現を使用して、部分文字列の完全一致の検索対象です。 検索が、静的に実行されます。<xref:System.Text.RegularExpressions.Regex.IsMatch%2A>メソッドで、2 つの文字列は入力として受け取ります。 1 つは、検索対象文字列、2 番目のパターンを検索します。

### <a name="example"></a>例

```cpp
// regex_simple.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
   array<String^>^ sentence =
   {
      "cow over the moon",
      "Betsy the Cow",
      "cowering in the corner",
      "no match here"
   };

   String^ matchStr = "cow";
   for (int i=0; i<sentence->Length; i++)
   {
      Console::Write( "{0,24}", sentence[i] );
      if ( Regex::IsMatch( sentence[i], matchStr,
                     RegexOptions::IgnoreCase ) )
         Console::WriteLine("  (match for '{0}' found)", matchStr);
      else
         Console::WriteLine("");
   }
   return 0;
}
```

## <a name="regex_extract"></a> 正規表現を使用して、データ フィールドを抽出するには

次のコード例では、書式設定された文字列からデータを抽出する正規表現の使用を示します。 次のコード例では、<xref:System.Text.RegularExpressions.Regex>クラスが電子メール アドレスに対応するパターンを指定します。 このパターンには、ユーザーとそれぞれの電子メール アドレスのホスト名の部分を取得するために使用するフィールドの識別子が含まれています。 <xref:System.Text.RegularExpressions.Match>クラスは、実際のパターン マッチングを実行するために使用します。 指定された電子メール アドレスが有効な場合、ユーザー名とホスト名が抽出されが表示されます。

### <a name="example"></a>例

```cpp
// Regex_extract.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
    array<String^>^ address=
    {
        "jay@southridgevideo.com",
        "barry@adatum.com",
        "treyresearch.net",
        "karen@proseware.com"
    };

    Regex^ emailregex = gcnew Regex("(?<user>[^@]+)@(?<host>.+)");

    for (int i=0; i<address->Length; i++)
    {
        Match^ m = emailregex->Match( address[i] );
        Console::Write("\n{0,25}", address[i]);

        if ( m->Success )
        {
            Console::Write("   User='{0}'",
            m->Groups["user"]->Value);
            Console::Write("   Host='{0}'",
            m->Groups["host"]->Value);
        }
        else
            Console::Write("   (invalid email address)");
        }

    Console::WriteLine("");
    return 0;
}
```

## <a name="regex_rearrange"></a> 正規表現を使用してデータを再配置

次のコード例では、.NET Framework 正規表現のサポートを使用して、再配置、またはデータを再フォーマットする方法を示します。 次のコード例では、<xref:System.Text.RegularExpressions.Regex>と<xref:System.Text.RegularExpressions.Match>クラスを文字列から最初と最後の名前を抽出し、逆の順序でこれらの要素の名前を表示します。

<xref:System.Text.RegularExpressions.Regex>クラスは、データの現在の形式を記述する正規表現を構築するために使用します。 2 つの名前はコンマで区切ると見なされ、どんな量のコンマの周囲の空白を使用することができます。 <xref:System.Text.RegularExpressions.Match>メソッドを使用して各文字列を分析します。 最初と最後の名前を取得、成功した場合、<xref:System.Text.RegularExpressions.Match>オブジェクトし、表示されます。

### <a name="example"></a>例

```cpp
// regex_reorder.cpp
// compile with: /clr
#using <System.dll>
using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ name =
   {
      "Abolrous, Sam",
      "Berg,Matt",
      "Berry , Jo",
      "www.contoso.com"
   };

   Regex^ reg = gcnew Regex("(?<last>\\w*)\\s*,\\s*(?<first>\\w*)");

   for ( int i=0; i < name->Length; i++ )
   {
      Console::Write( "{0,-20}", name[i] );
      Match^ m = reg->Match( name[i] );
      if ( m->Success )
      {
         String^ first = m->Groups["first"]->Value;
         String^ last = m->Groups["last"]->Value;
         Console::WriteLine("{0} {1}", first, last);
      }
      else
         Console::WriteLine("(invalid)");
   }
   return 0;
}
```

## <a name="regex_search"></a> 正規表現を使用して、検索し、置換するには

次のコード例に示す方法、正規表現クラス<xref:System.Text.RegularExpressions.Regex>検索と置換を実行するために使用できます。 これは、<xref:System.Text.RegularExpressions.Regex.Replace%2A>メソッド。 使用されているバージョンは、入力として 2 つの文字列: 文字列を変更して (あれば) セクションでは、代わりに挿入する文字列に指定されたパターンに一致する、<xref:System.Text.RegularExpressions.Regex>オブジェクト。

このコードは、文字列内のすべての数字をアンダー スコア (_) に置き換え、ものを削除することは実質的に、空の文字列に置き換えます。 1 つの手順では、同じ効果を実行できますが、デモンストレーションのために 2 つの手順をここでも使用されます。

### <a name="example"></a>例

```cpp
// regex_replace.cpp
// compile with: /clr
#using <System.dll>
using namespace System::Text::RegularExpressions;
using namespace System;

int main()
{
   String^ before = "The q43uick bro254wn f0ox ju4mped";
   Console::WriteLine("original  : {0}", before);

   Regex^ digitRegex = gcnew Regex("(?<digit>[0-9])");
   String^ after = digitRegex->Replace(before, "_");
   Console::WriteLine("1st regex : {0}", after);

   Regex^ underbarRegex = gcnew Regex("_");
   String^ after2 = underbarRegex->Replace(after, "");
   Console::WriteLine("2nd regex : {0}", after2);

   return 0;
}
```

## <a name="regex_validate"></a> 正規表現を使用して、データの書式設定を検証するには

次のコード例では、文字列の書式設定を検証する正規表現の使用を示します。 次のコード例では、文字列は有効な電話番号を含める必要があります。 次のコード例は、文字列を使用して"\d{3}-\d{3}-\d{4}"を示す各フィールドが有効な電話番号を表します。 文字列"d"は数字を示し、"d"の後の引数が存在する必要がある数字の数を示します。 この場合は、数がハイフンで区切る必要です。

### <a name="example"></a>例

```cpp
// regex_validate.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ number =
   {
      "123-456-7890",
      "444-234-22450",
      "690-203-6578",
      "146-893-232",
      "146-839-2322",
      "4007-295-1111",
      "407-295-1111",
      "407-2-5555",
   };

   String^ regStr = "^\\d{3}-\\d{3}-\\d{4}$";

   for ( int i = 0; i < number->Length; i++ )
   {
      Console::Write( "{0,14}", number[i] );

      if ( Regex::IsMatch( number[i], regStr ) )
         Console::WriteLine(" - valid");
      else
         Console::WriteLine(" - invalid");
   }
   return 0;
}
```

## <a name="related-sections"></a>関連項目

[.NET Framework 正規表現](/dotnet/standard/base-types/regular-expressions)

## <a name="see-also"></a>関連項目

[C++/CLI (Visual C++) による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
