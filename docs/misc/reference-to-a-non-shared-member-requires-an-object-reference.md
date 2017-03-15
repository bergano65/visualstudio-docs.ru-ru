---
title: "Для ссылки на член, не являющийся общим, требуется ссылка на объект | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30469"
  - "vbc30469"
helpviewer_keywords: 
  - "BC30469"
ms.assetid: af503e8b-2e1f-4f91-a07f-b1ddd73dd4a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Для ссылки на член, не являющийся общим, требуется ссылка на объект
В коде имеется ссылка на член, не являющийся общим, и не удалось предоставить ссылку на объект. Нельзя использовать имя самого класса для уточнения члена, который не является общим. Экземпляр сначала должен быть объявлен как объектная переменная, а затем можно ссылаться на него по имени этой переменной.  
  
 **Идентификатор ошибки:** BC30469  
  
### Исправление ошибки  
  
1.  Объявите экземпляр как объектную переменную.  
  
2.  Ссылайтесь на экземпляр по имени этой переменной.  
  
## См. также  
 [НЕ В СБОРКЕ. Общие сведения о классах](http://msdn.microsoft.com/ru-ru/cc2355a2-cb98-4353-9440-736585aec46c)   
 [НЕ В СБОРКЕ. Общие члены в Visual Basic](http://msdn.microsoft.com/ru-ru/dbc3783f-83a2-4225-995d-c2d6d025663d)   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [НЕ В СБОРКЕ. Разрешение ссылки, когда несколько переменных имеют одинаковые имена](http://msdn.microsoft.com/ru-ru/9601e39f-1911-44e1-ace5-3f6e090408b9)