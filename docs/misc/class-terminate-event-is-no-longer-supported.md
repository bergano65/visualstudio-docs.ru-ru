---
title: "Событие Class_Terminate больше не поддерживается | Microsoft Docs"
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
  - "vbc42002"
  - "bc42002"
helpviewer_keywords: 
  - "BC42002"
ms.assetid: 11eeac74-666d-4b23-81bc-b1691290ddd0
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Событие Class_Terminate больше не поддерживается
Событие Class\_Terminate больше не поддерживается. Для освобождения ресурсов используйте процедуру Sub Finalize.  
  
 Событие `Class_Terminate`, имевшееся в предыдущих версиях Visual Basic, заменено деструкторами классов.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42002  
  
### Исправление ошибки  
  
-   Объявите процедуру `Sub` с именем `Finalize` для уничтожения класса.`Sub Finalize` вызывается, если сборщик мусора обнаруживает, что больше не существует активных ссылок на экземпляр.  
  
## См. также  
 [Classes for Visual Basic 6.0 Users](http://msdn.microsoft.com/ru-ru/d625222c-cd32-4c8d-b25c-ea71729b88b7)   
 [НЕ В СБОРКЕ. Использование конструкторов и деструкторов](http://msdn.microsoft.com/ru-ru/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [НЕ В СБОРКЕ. Практическое руководство. Реализация схемы Dispose Finalize \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/adf7a232-4ebb-485d-8626-8d64421eb0c4)