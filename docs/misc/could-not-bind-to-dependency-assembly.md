---
title: "Could not bind to dependency &#39;assembly&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cantbinddependency"
ms.assetid: 0f76190d-d57e-4e0e-bec4-532aec978d08
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not bind to dependency &#39;assembly&#39;
Одна из ссылок проекта сама содержит ссылку на сборку \(зависимость\), причем эта сборка найдена, но не является допустимой.  Эта ошибка не останавливает построение проекта.  Однако может возникать ошибка времени выполнения.  
  
 В данной ситуации имеет место совпадение трех перечисленных ниже условий.  
  
-   На диске существует как минимум два файла с одинаковыми именами.  
  
-   Один из этих файлов является сборкой, а другой — нет.  
  
-   В путях ссылок первым указана папка, которая содержит файл, не являющийся сборкой.  
  
 **Чтобы исправить эту ошибку**  
  
-   Измените порядок, в котором проект осуществляет поиск ссылок по папкам.  Дополнительные сведения см. в разделе [NIB: Reference Paths Dialog Box \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/8e549b39-7256-456a-8fd7-089b23facf9c).  
  
## См. также  
 [Диагностика неработающих ссылок](../ide/troubleshooting-broken-references.md)   
 [Практическое руководство. Добавление и удаление ссылок с помощью диалогового окна "Добавление ссылок"](http://msdn.microsoft.com/ru-ru/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/ru-ru/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)