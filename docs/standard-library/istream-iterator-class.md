---
title: "istream_iterator Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "iterator/std::istream_iterator"
  - "std.istream_iterator"
  - "std::istream_iterator"
  - "istream_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "istream_iterator class"
ms.assetid: fb52a8cd-7f71-48d1-b73e-4b064e2a8d16
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# istream_iterator Class
Describes an input iterator object. It extracts objects of class `Type` from an input stream, which it accesses through an object it stores, of type `pointer` to `basic_istream`< `CharType`, `Traits`>.  
  
## Syntax  
  
```
template <class Type, class CharType = char, class Traits = char_traits<CharType>, class Distance = ptrdiff_t,>  
class istream_iterator
 : public iterator<
    input_iterator_tag, Type, Distance,
    const Type *,
    const Type&>;
```  
  
#### Parameters  
 `Type`  
 The type of object to be extracted from the input stream.  
  
 `CharType`  
 The type that represents the character type for the `istream_iterator`. This argument is optional and the default value is `char`.  
  
 `Traits`  
 The type that represents the character type for the `istream_iterator`. This argument is optional and the default value is `char_traits`< `CharType`>.  
  
 `Distance`  
 A signed integral type that represents the difference type for the `istream_iterator`. This argument is optional and the default value is `ptrdiff_t`.  
  
 After constructing or incrementing an object of class istream_iterator with a nonnull stored pointer, the object attempts to extract and store an object of type `Type` from the associated input stream. If the extraction fails, the object effectively replaces the stored pointer with a null pointer, thus making an end-of-sequence indicator.  
  
### Constructors  
  
|||  
|-|-|  
|[istream_iterator](#istream_iterator__istream_iterator)|Constructs either an end-of-stream iterator as the default `istream_iterator` or a `istream_iterator` initialized to the iterator's stream type from which it reads.|  
  
### Typedefs  
  
|||  
|-|-|  
|[char_type](#istream_iterator__char_type)|A type that provides for the character type of the `istream_iterator`.|  
|[istream_type](#istream_iterator__istream_type)|A type that provides for the stream type of the `istream_iterator`.|  
|[traits_type](#istream_iterator__traits_type)|A type that provides for the character traits type of the `istream_iterator`.|  
  
### Operators  
  
|||  
|-|-|  
|[operator*](#istream_iterator__operator_star)|The dereferencing operator returns the stored object of type `Type` addressed by the `istream_iterator`.|  
|[operator->](#istream_iterator__operator-_gt_)|Returns the value of a member, if any.|  
|[operator++](#istream_iterator__operator_add_add)|Either extracts an incremented object from the input stream or copies the object before incrementing it and returns the copy.|  
  
## Requirements  
 **Header:** \<iterator>  
  
 **Namespace:** std  
  
##  <a name="istream_iterator__char_type"></a>  istream_iterator::char_type  
 A type that provides for the character type of the `istream_iterator`.  
  
```
typedef CharType char_type;
```  
  
### Remarks  
 The type is a synonym for the template parameter **Chartype**.  
  
### Example  
  
```cpp  
// istream_iterator_char_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   typedef istream_iterator<int>::char_type CHT1;  
   typedef istream_iterator<int>::traits_type CHTR1;  
  
   // Standard iterator interface for reading  
   // elements from the input stream:  
   cout << "Enter integers separated by spaces & then\n"  
        << " any character ( try example: '2 4 f' ): ";  
  
   // istream_iterator for reading int stream  
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );  
  
   // End-of-stream iterator  
   istream_iterator<int, CHT1, CHTR1> EOFintRead;  
  
   while ( intRead != EOFintRead )  
   {  
      cout << "Reading:  " << *intRead << endl;  
      ++intRead;  
   }  
   cout << endl;  
}  
```  
  
##  <a name="istream_iterator__istream_iterator"></a>  istream_iterator::istream_iterator  
 Constructs either an end-of-stream iterator as the default `istream_iterator` or a `istream_iterator` initialized to the iterator's stream type from which it reads.  
  
```
istream_iterator();

istream_iterator(istream_type& _Istr);
```  
  
### Parameters  
 `_Istr`  
 The input stream to be read use to initialize the `istream_iterator`.  
  
### Remarks  
 The First constructor initializes the input stream pointer with a null pointer and creates an end-of-stream iterator. The second constructor initializes the input stream pointer with *&_Istr*, then attempts to extract and store an object of type **Type**.  
  
 The end-of-stream iterator can be use to test whether an `istream_iterator` has reached the end of a stream.  
  
### Example  
  
```cpp  
// istream_iterator_istream_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Used in conjunction with copy algorithm  
   // to put elements into a vector read from cin  
   vector<int> vec ( 4 );  
   vector <int>::iterator Iter;  
  
   cout << "Enter 4 integers separated by spaces & then\n"  
        << " a character ( try example: '2 4 6 8 a' ): ";  
   istream_iterator<int> intvecRead ( cin );  
  
   // Default constructor will test equal to end of stream  
   // for delimiting source range of vecor  
   copy ( intvecRead , istream_iterator<int>( ) , vec.begin ( ) );  
   cin.clear ( );  
  
   cout << "vec = ";  
   for ( Iter = vec.begin( ) ; Iter != vec.end( ) ; Iter++ )  
      cout << *Iter << " "; cout << endl;  
}  
```  
  
##  <a name="istream_iterator__istream_type"></a>  istream_iterator::istream_type  
 A type that provides for the stream type of the `istream_iterator`.  
  
```
typedef basic_istream<CharType, Traits> istream_type;
```  
  
### Remarks  
 The type is a synonym for `basic_istream`\< **CharType**, **Traits**>.  
  
### Example  
  See [istream_iterator](#istream_iterator__istream_iterator) for an example of how to declare and use `istream_type`.  
  
##  <a name="istream_iterator__operator_star"></a>  istream_iterator::operator*  
 The dereferencing operator returns the stored object of type **Type** addressed by the `istream_iterator`.  
  
```
const Type& operator*() const;
```  
  
### Return Value  
 The stored object of type **Type**.  
  
### Example  
  
```cpp  
// istream_iterator_operator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   cout << "Enter integers separated by spaces & then\n"  
        << " a character ( try example: '2 4 6 8 a' ): ";  
  
   // istream_iterator from stream cin  
   istream_iterator<int> intRead ( cin );  
  
   // End-of-stream iterator  
   istream_iterator<int> EOFintRead;  
  
   while ( intRead != EOFintRead )  
   {  
      cout << "Reading:  " << *intRead << endl;  
      ++intRead;  
   }  
   cout << endl;  
}  
```  
  
##  <a name="istream_iterator__operator-_gt_"></a>  istream_iterator::operator-&gt;  
 Returns the value of a member, if any.  
  
```
const Type* operator->() const;
```  
  
### Return Value  
 The value of a member, if any.  
  
### Remarks  
 *i* -> is equivalent to (\* *i*). *m*  
  
 The operator returns **&\*\*this**.  
  
### Example  
  
```cpp  
// istream_iterator_operator_vm.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>  
#include <complex>  
  
using namespace std;  
  
int main( )  
{  
   cout << "Enter complex numbers separated by spaces & then\n"  
        << " a character pair ( try example: '(1,2) (3,4) (a,b)' ): ";  
  
   // istream_iterator from stream cin  
   istream_iterator< complex<double> > intRead ( cin );  
  
   // End-of-stream iterator  
   istream_iterator<complex<double> > EOFintRead;  
  
   while ( intRead != EOFintRead )  
   {  
      cout << "Reading the real part: " << intRead ->real( ) << endl;  
      cout << "Reading the imaginary part: " << intRead ->imag( ) << endl;  
      ++intRead;  
   }  
   cout << endl;  
}  
```  
  
##  <a name="istream_iterator__operator_add_add"></a>  istream_iterator::operator++  
 Either extracts an incremented object from the input stream or copies the object before incrementing it and returns the copy.  
  
```
istream_iterator<Type, CharType, Traits, Distance>& operator++();

istream_iterator<Type, CharType, Traits, Distance> operator++(int);
```  
  
### Return Value  
 The first member operator returns a reference to the incremented object of type **Type** extracted from the input stream and the second member function returns a copy of the object.  
  
### Example  
  
```cpp  
// istream_iterator_operator_incr.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   cout << "Enter integers separated by spaces & then\n"  
        << " a character ( try example: '2 4 6 8 a' ): ";  
  
   // istream_iterator from stream cin  
   istream_iterator<int> intRead ( cin );  
  
   // End-of-stream iterator  
   istream_iterator<int> EOFintRead;  
  
   while ( intRead != EOFintRead )  
   {  
      cout << "Reading:  " << *intRead << endl;  
      ++intRead;  
   }  
   cout << endl;  
}  
```  
  
##  <a name="istream_iterator__traits_type"></a>  istream_iterator::traits_type  
 A type that provides for the character traits type of the `istream_iterator`.  
  
```
typedef Traits traits_type;
```  
  
### Remarks  
 The type is a synonym for the template parameter **Traits**.  
  
### Example  
  
```cpp  
// istream_iterator_traits_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   typedef istream_iterator<int>::char_type CHT1;  
   typedef istream_iterator<int>::traits_type CHTR1;  
  
   // Standard iterator interface for reading  
   // elements from the input stream:  
   cout << "Enter integers separated by spaces & then\n"  
        << " any character ( try example: '10 20 a' ): ";  
  
   // istream_iterator for reading int stream  
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );  
  
   // End-of-stream iterator  
   istream_iterator<int, CHT1, CHTR1> EOFintRead;  
  
   while ( intRead != EOFintRead )  
   {  
      cout << "Reading:  " << *intRead << endl;  
      ++intRead;  
   }  
   cout << endl;  
}  
```  
  
## See Also  
 [input_iterator_tag Struct](../standard-library/input-iterator-tag-struct.md)   
 [iterator Struct](../standard-library/iterator-struct.md)   
 [\<iterator>](../standard-library/iterator.md)   
 [Thread Safety in the C++ Standard Library](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standard Template Library](../misc/standard-template-library.md)


