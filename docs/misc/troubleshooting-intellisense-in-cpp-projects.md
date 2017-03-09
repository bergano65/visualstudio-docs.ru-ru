---
title: "Устранение неполадок в технологии IntelliSense в проектах C++ | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NCB-файлы"
  - "IntelliSense, устранение неполадок в проектах C++"
  - "NCB-файлы"
  - "устранение неполадок IntelliSense"
  - "устранение неполадок - Visual C++, IntelliSense"
ms.assetid: 72e4eb39-66d3-403d-8da7-00ed288a1899
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Устранение неполадок в технологии IntelliSense в проектах C++
Технология IntelliSense может прекратить работать при определенных условиях.  Следующая процедура поможет определить, почему IntelliSense не работает с проектами С\+\+.  
  
### Изучение сбоев IntelliSense в проектах С\+\+  
  
1.  Убедитесь, что в проекте Visual C\+\+ отсутствуют ошибки компиляции.  
  
    1.  Если речь идет о проекте Makefile, см. раздел [Практическое руководство. Использование IntelliSense для проекта Makefile](../Topic/How%20to:%20Enable%20IntelliSense%20for%20Makefile%20Projects.md).  
  
2.  Убедитесь, что файл stdafx.h находится на пути включения.  Дополнительные сведения о путях включения в проектах Visual C\+\+ см. в разделах [Директива \#include](/visual-cpp/preprocessor/hash-include-directive-c-cpp) и [\/I \(дополнительные каталоги включения\)](/visual-cpp/build/reference/i-additional-include-directories).  
  
## Ограничения технологии IntelliSense  
 Технология IntelliSense не работает в проектах C\+\+ в следующих случаях:  
  
-   Курсор находится в комментарии к коду.  
  
-   Создается строковый литерал.  
  
-   Над курсором отображается синтаксическая ошибка.  
  
-   Решение состоит либо из синтаксиса управляемого кода С\+\+, либо из более ранних управляемых расширений синтаксиса С\+\+.  
  
-   IntelliSense не полностью поддерживается при наличии нескольких ссылок на файл заголовка с использованием директивы `#include` и изменении значения этого файла заголовка из\-за разных состояний макроса, определенных с помощью директивы `#define`.  Другими словами, при многократном включении файла заголовка и изменении способов использования заголовка при разных состояниях макроса IntelliSense работает не всегда.  
  
## См. также  
 [Troubleshooting IntelliSense](http://msdn.microsoft.com/ru-ru/c1b3adb9-0d48-4770-a51e-392ed818c484)   
 [Практическое руководство. Организация выходных файлов проекта для построения](../Topic/How%20to:%20Organize%20Project%20Output%20Files%20for%20Builds.md)