---
title: "Член &quot;&lt;член&gt;&quot; конфликтует с зарезервированным членом по данному имени, которое неявно объявлено во всех перечислениях. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31420"
  - "vbc31420"
helpviewer_keywords: 
  - "BC31420"
ms.assetid: f2ea5a8b-f63c-4c93-bfac-418ae5a150a5
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Член &quot;&lt;член&gt;&quot; конфликтует с зарезервированным членом по данному имени, которое неявно объявлено во всех перечислениях.
Имя члена типа конфликтует с именем члена, неявно объявленного во всех перечислениях.  
  
 Компилятор [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] создает неявные члены, соответствующие определенным программным элементам, которые вы объявляете. Перечисления неявно объявляют элемент `value__member`.  
  
 **Идентификатор ошибки:** BC31420  
  
### Исправление ошибки  
  
-   Измените имя элемента.  
  
## См. также  
 [НЕ В СБОРКЕ. Операторы объявления в Visual Basic](http://msdn.microsoft.com/ru-ru/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [Общие сведения о перечислениях](/dotnet/visual-basic/programming-guide/language-features/constants-enums/enumerations-overview)   
 [Имена объявленных элементов](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)