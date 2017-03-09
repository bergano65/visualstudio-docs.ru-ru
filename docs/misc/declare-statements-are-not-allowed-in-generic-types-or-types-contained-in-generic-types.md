---
title: "Операторы Declare нельзя использовать в универсальных типах и типах, содержащихся в универсальных типах | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC32075"
  - "vbc32075"
helpviewer_keywords: 
  - "BC32075"
ms.assetid: c620b67e-70f8-42ac-8292-e9ea484904c3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операторы Declare нельзя использовать в универсальных типах и типах, содержащихся в универсальных типах
Оператор `Declare` используется как часть универсального класса или структуры, либо класс или структура объявлены в универсальном классе или структуре.  
  
 Visual Basic и .NET Framework в настоящее время не поддерживают каких\-либо сочетаний внешних ссылок и универсальных типов. Компилятору для формирования правильного вызова нужны все параметры и тип возвращаемого значения внешней процедуры.  
  
 **Идентификатор ошибки:** BC32075  
  
### Исправление ошибки  
  
-   Переместите оператор `Declare` за пределы области видимости всех универсальных типов или удалите его.  
  
## См. также  
 [Оператор Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)