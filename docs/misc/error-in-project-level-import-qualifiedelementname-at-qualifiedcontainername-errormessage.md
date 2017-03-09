---
title: "Ошибка при импорте на уровне проекта &quot;&lt;полное_имя_элемента&gt;&quot; в &quot;&lt;полное_имя_контейнера&gt;&quot;: &quot;&lt;сообщение_об_ошибке&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC30797"
  - "vbc30797"
helpviewer_keywords: 
  - "BC30797"
ms.assetid: 529f354f-f255-4adc-ab21-bd1796e58d69
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ошибка при импорте на уровне проекта &quot;&lt;полное_имя_элемента&gt;&quot; в &quot;&lt;полное_имя_контейнера&gt;&quot;: &quot;&lt;сообщение_об_ошибке&gt;&quot;
Инструкция обращается к программному элементу, который определен в другой сборке, но нет ссылки проекта на эту сборку.  
  
 Например, код может обращаться к перечислению с именем `desiredEnumeration` с помощью уточняющей строки `otherNamespace.otherClass.desiredEnumeration`. Если компилятор не может найти `otherNamespace.otherClass` среди ссылок проекта, он выдает эту ошибку.  
  
 **Идентификатор ошибки:** BC30797  
  
### Исправление ошибки  
  
1.  Убедитесь, что каждый элемент в уточняющей строке программного элемента указан правильно.  
  
2.  Убедитесь, что проект содержит ссылку на сборку, определяющую нужный программный элемент.  
  
3.  Проверьте указанное сообщение об ошибке и предпримите соответствующее действие.  
  
## См. также  
 [НЕ В СБОРКЕ. Разрешение ссылки, когда несколько переменных имеют одинаковые имена](http://msdn.microsoft.com/ru-ru/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NIB. Практическое руководство. Изменение свойств проекта и параметров конфигурации](http://msdn.microsoft.com/ru-ru/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [NIB. Практическое руководство. Добавление и удаление ссылок с помощью диалогового окна "Добавление ссылки"](http://msdn.microsoft.com/ru-ru/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)