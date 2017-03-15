---
title: "Метод доступа &quot;&lt;ключевое_слово&gt;&quot; для &quot;&lt;имя_свойства&gt;&quot; устарел (предупреждение Visual Basic) | Microsoft Docs"
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
  - "vbc40020"
  - "bc40020"
helpviewer_keywords: 
  - "BC40020"
ms.assetid: 005440f4-6e82-421c-b2ce-9c5139325bac
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод доступа &quot;&lt;ключевое_слово&gt;&quot; для &quot;&lt;имя_свойства&gt;&quot; устарел (предупреждение Visual Basic)
Оператор пытается прочитать или записать свойство, для которого соответствующая процедура была помечена атрибутом <xref:System.ObsoleteAttribute>; в этой ситуации компилятор выдает предупреждение.  
  
 Вы можете пометить любой программный элемент как неиспользуемый, применив к нему <xref:System.ObsoleteAttribute>. В этом случае можно задать для свойства <xref:System.ObsoleteAttribute.IsError%2A> атрибута значение `True` или `False`. При задании значения `True` компилятор будет рассматривать попытку использовать элемент как ошибку. Если задать значение `False` или оставить значение по умолчанию `False`, то при попытке использовать элемент компилятор выдаст предупреждение.  
  
 По умолчанию это сообщение считается предупреждением, так как свойство <xref:System.ObsoleteAttribute.IsError%2A><xref:System.ObsoleteAttribute> имеет значение `False`. Дополнительные сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40020  
  
### Исправление ошибки  
  
1.  Убедитесь, что имя свойства в исходном коде написано правильно.  
  
2.  Избегайте доступа к свойству способом \(чтение или запись\), который приводит к возникновению этого сообщения.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)