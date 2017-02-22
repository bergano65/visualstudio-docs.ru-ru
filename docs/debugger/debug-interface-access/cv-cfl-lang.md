---
title: "CV_CFL_LANG | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CV_CFL_LANG - перечисление"
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CV_CFL_LANG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Задает язык исходного кода приложения или связанного модуля.  
  
## Синтаксис  
  
```cpp#  
typedef enum CV_CFL_LANG {   
   CV_CFL_C       = 0x00,  
   CV_CFL_CXX     = 0x01,  
   CV_CFL_FORTRAN = 0x02,  
   CV_CFL_MASM    = 0x03,  
   CV_CFL_PASCAL  = 0x04,  
   CV_CFL_BASIC   = 0x05,  
   CV_CFL_COBOL   = 0x06,  
   CV_CFL_LINK    = 0x07,  
   CV_CFL_CVTRES  = 0x08,  
   CV_CFL_CVTPGD  = 0x09,  
   CV_CFL_CSHARP  = 0x0A,  
   CV_CFL_VB      = 0x0B,  
   CV_CFL_ILASM   = 0x0C,  
   CV_CFL_JAVA    = 0x0D,  
   CV_CFL_JSCRIPT = 0x0E,  
   CV_CFL_MSIL    = 0x0F,  
   CV_CFL_HLSL    = 0x10  
} CV_CFL_LANG;  
```  
  
## Elements  
 CV\_CFL\_C  
 Язык приложения c\#.  
  
 CV\_CFL\_CXX  
 Язык приложения C\+\+.  
  
 CV\_CFL\_FORTRAN  
 Язык приложения FORTRAN.  
  
 CV\_CFL\_MASM  
 Язык приложения ассемблер макроса Майкрософт.  
  
 CV\_CFL\_PASCAL  
 Язык pascal приложения.  
  
 CV\_CFL\_BASIC  
 Язык ОСНОВНОГО приложения.  
  
 CV\_CFL\_COBOL  
 Язык COBOL приложения.  
  
 CV\_CFL\_LINK  
 Приложение компоновщик\- созданный модуль.  
  
 CV\_CFL\_CVTRES  
 Приложение модуль ресурса преобразованный со средством CVTRES.  
  
 CV\_CFL\_CVTPGD  
 Приложение модуль оптимизированного POGO, созданный с помощью средства CVTPGD.  
  
 CV\_CFL\_CSHARP  
 Язык приложения C\#.  
  
 CV\_CFL\_VB  
 Язык приложения Visual Basic.  
  
 CV\_CFL\_ILASM  
 Язык приложения сборки промежуточного языка \(т е сборки среды CLR\).  
  
 CV\_CFL\_JAVA  
 Язык приложения Java.  
  
 CV\_CFL\_JSCRIPT  
 Язык приложения Jscript.  
  
 CV\_CFL\_MSIL  
 Язык приложения неизвестное MSIL, возможно, результат использования переключателя [Параметр \/LTCG \(создание кода во время компоновки\)](/visual-cpp/build/reference/ltcg-link-time-code-generation).  
  
 CV\_CFL\_HLSL  
 Язык приложения общий язык шейдера.  
  
## Заметки  
 Значения в этом перечислении возвращаемых вызовом метода [IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md).  
  
## Требования  
 Заголовок: cvconst.h  
  
## См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md)