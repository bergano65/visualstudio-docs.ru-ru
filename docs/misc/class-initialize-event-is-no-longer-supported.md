---
title: "Событие Class_Initialize больше не поддерживается | Microsoft Docs"
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
  - "vbc42001"
  - "bc42001"
helpviewer_keywords: 
  - "BC42001"
ms.assetid: 31e7c383-894e-416c-b834-3688cc340ccf
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Событие Class_Initialize больше не поддерживается
Событие Class\_Initialize больше не поддерживается. Используйте Sub New для инициализации класса.  
  
 Событие `Class_Initialize`, имевшееся в предыдущих версиях [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], заменено конструкторами классов.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42001  
  
### Исправление ошибки  
  
-   Объявить одну или несколько процедур `Sub` с именами `New` для инициализации класса.`Sub New` вызывается при создании нового экземпляра класса.  
  
## См. также  
 [Class\_Initialize Changes in Visual Basic](http://msdn.microsoft.com/ru-ru/2cd023cf-2869-4836-b08d-43822294beeb)   
 [Classes for Visual Basic 6.0 Users](http://msdn.microsoft.com/ru-ru/d625222c-cd32-4c8d-b25c-ea71729b88b7)   
 [НЕ В СБОРКЕ. Использование конструкторов и деструкторов](http://msdn.microsoft.com/ru-ru/548eebe1-86c4-4377-b2f5-447cb8be3d90)