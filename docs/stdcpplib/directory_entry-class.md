---
title: "directory_entry Class"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
f1_keywords: 
  - "filesystem/std::tr2::sys::directory_entry"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator const std::experimental::filesystem::v1::path &"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::directory_entry"
  - "std::experimental::filesystem::v1::directory_entry::directory_entry"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator="
  - "std::experimental::filesystem::v1::directory_entry::operator="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::assign"
  - "std::experimental::filesystem::v1::directory_entry::assign"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::replace_filename"
  - "std::experimental::filesystem::v1::directory_entry::replace_filename"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::path"
  - "std::experimental::filesystem::v1::directory_entry::path"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::status"
  - "std::experimental::filesystem::v1::directory_entry::status"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::symlink_status"
  - "std::experimental::filesystem::v1::directory_entry::symlink_status"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator<"
  - "std::experimental::filesystem::v1::directory_entry::operator<"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator=="
  - "std::experimental::filesystem::v1::directory_entry::operator=="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator!="
  - "std::experimental::filesystem::v1::directory_entry::operator!="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator<="
  - "std::experimental::filesystem::v1::directory_entry::operator<="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator>"
  - "std::experimental::filesystem::v1::directory_entry::operator>"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator>="
  - "std::experimental::filesystem::v1::directory_entry::operator>="
dev_langs: 
  - "C++"
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
caps.latest.revision: 16
ms.author: "corob"
manager: "ghogen"
translation.priority.mt: 
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
# directory_entry Class
Describes an object that is returned by `*X`, where *X* is a [directory_iterator](../stdcpplib/directory_iterator-class.md) or a [recursive_directory_iterator](../stdcpplib/recursive_directory_iterator-class.md).  
  
## Syntax  
  
```  
class directory_entry;  
```  
  
## Remarks  
 The class stores an object of type [path](../stdcpplib/path-class--c---standard-template-library-.md). The stored `path` can be an instance of the [path Class](../stdcpplib/path-class--c---standard-template-library-.md) or of a type that is derived from `path`. It also stores two [file_type](../Topic/file_type%20Enumeration.md) values; one that represents what is known about the status of the stored file name, and another that represents what is known about the symbolic link status of the file name.  
  
 For more information and code examples, see [File System Navigation (C++)](../stdcpplib/file-system-navigation.md).  
  
## assign  
  
```  
void assign(const std::experimental::filesystem::v1::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());  
```  
  
 The member function assigns pval to mypath, stat to mystat, and symstat to mysymstat.  
  
## directory_entry  
  
```  
directory_entry() = default;  
directory_entry(const directory_entry&) = default;  
directory_entry(directory_entry&&) noexcept = default;  
explicit directory_entry(const std::experimental::filesystem::v1::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());  
```  
  
 The defaulted constructors behave as expected. The fourth constructor initializes mypath to pval, mystat to stat_arg, and mysymstat to symstat_arg.  
  
## operator!=  
  
```  
bool operator!=(const directory_entry& right) const noexcept;  
  
```  
  
 The member function returns !(*this == right).  
  
## operator=  
  
```  
directory_entry& operator=(const directory_entry&) = default;  
directory_entry& operator=(directory_entry&&) noexcept = default;  
  
```  
  
 The defaulted member assignment operators behave as expected.  
  
## operator==  
  
```  
bool operator==(const directory_entry& right) const noexcept;  
```  
  
 The member function returns mypath == right.mypath.  
  
## operator<  
  
```  
  
bool operator<(const directory_entry& right) const noexcept;  
  
```  
  
 The member function returns mypath < right.mypath.  
  
## operator<=  
  
```  
bool operator<=(const directory_entry& right) const noexcept;  
```  
  
 The member function returns !(right \< *this).  
  
## operator>  
  
```  
bool operator>(const directory_entry& right) const noexcept;  
```  
  
 The member function returns right \< *this.  
  
## operator>=  
  
```  
bool operator>=(const directory_entry& right) const noexcept;  
  
```  
  
 The member function returns !(*this < right).  
  
## operator const path_type&  
  
```  
operator const std::experimental::filesystem::v1::path&() const; // retained  
```  
  
 The member operator returns mypath.  
  
## path  
  
```  
const std::experimental::filesystem::v1::path& path() const noexcept;  
```  
  
 The member function returns mypath.  
  
## replace_filename  
  
```  
void replace_filename(const std::experimental::filesystem::v1::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());  
```  
  
 The member function replaces mypath with mypath.parent_path() / pval, mystat with stat_arg, and mysymstat with symstat_arg  
  
## status  
  
```  
file_status status() const;  
file_status status(  
    error_code& ec) const noexcept;  
Otherwise, mystat = status(mypval).  
  
```  
  
 Both member functions return mystat possibly first altered as follows:  
  
1.  If status_known(mystat) then do nothing.  
  
2.  Otherwise, if !status_known(mysymstat) && !is_symlink(mysymstat) then mystat = mysymstat.  
  
## symlink_status  
  
```  
file_status symlink_status() const;  
file_status symlink_status(  
    error_code& ec) const noexcept;  
```  
  
 Both member functions return mysymstat possibly first altered as follows:If status_known(mysymstat) then do nothing. Otherwise, mysymstat = symlink_status(mypval).  
  
## Requirements  
 **Header:** \<experimental/filesystem>  
  
 **Namespace:** std::experimental::filesystem::v1  
  
## See Also  
 [Header Files Reference](../stdcpplib/c---standard-library-header-files.md)   
 [\<filesystem>](../stdcpplib/-filesystem-.md)