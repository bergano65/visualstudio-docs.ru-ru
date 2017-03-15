---
title: "An error has been encountered that prevents reference &#39;reference&#39; from loading. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.reference_load_error"
ms.assetid: 0e922611-197b-4607-bc31-03f80bd3e7e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# An error has been encountered that prevents reference &#39;reference&#39; from loading. &lt;reason&gt;
Произошла неустранимая ошибка при удалении ссылки из файла проекта.  Причины этой ошибки определены в строке \<причина\> и указаны ниже.  
  
-   Неправильно сформированный идентификатор GUID для ссылки.  Это относится только к ссылкам модели COM.  
  
-   Неверное средство создания программ\-оболочек.  В настоящий момент свойство WrapperTool может принимать только значения "tlbimp", "aximp" или "primary".  Это относится только к ссылкам модели COM.  
  
-   Неверная строка ссылки на проект.  Это относится только к ссылкам между проектами.  
  
 **Чтобы исправить эту ошибку**  
  
-   Добавьте в проект правильную ссылку.  
  
     Ссылка, для которой отображается это диагностическое сообщение, не будет загружена в проект.  
  
## См. также  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ru-ru/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)