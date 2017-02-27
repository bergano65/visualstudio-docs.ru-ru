---
title: "NameSearchOptions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NameSearchOptions - перечисление"
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# NameSearchOptions
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Задает параметры поиска символов и имен файлов.  
  
## Синтаксис  
  
```cpp#  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## Elements  
 `nsNone`  
 Параметры не указаны.  
  
 `nsfCaseSensitive`  
 Применяет с учетом регистра соответствие имени.  
  
 `nsfCaseInsensitive`  
 Применяет без учета регистра соответствие имени.  
  
 `nsfFNameExt`  
 Рассматривает имена в виде путей и применяет сопоставление имени filename.ext.  
  
 `nsfRegularExpression`  
 Применяет с учетом регистра соответствие имени использование звездочки \(\*\) и вопросительные знаки \(?\) в качестве подстановочные знаки.  
  
 `nsfUndecoratedName`  
 Применяется только к символам, которые имеют упрощенного и внутренние имена.  
  
## Заметки  
 Значения из этого перечисления передается следующим приемам:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## Требования  
 Заголовок: dia2.h  
  
## См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)