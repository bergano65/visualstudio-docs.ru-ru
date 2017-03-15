---
title: "Метод доступа &quot;&lt;ключевое_слово&gt;&quot; свойства &quot;&lt;имя_свойства&gt;&quot; устарел: &quot;&lt;сообщение_об_ошибке&gt;&quot; (предупреждение Visual Basic) | Microsoft Docs"
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
  - "bc40019"
  - "vbc40019"
helpviewer_keywords: 
  - "BC40019"
ms.assetid: 57d00655-1837-4605-a5e9-1ae5b6935f51
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод доступа &quot;&lt;ключевое_слово&gt;&quot; свойства &quot;&lt;имя_свойства&gt;&quot; устарел: &quot;&lt;сообщение_об_ошибке&gt;&quot; (предупреждение Visual Basic)
Оператор пытается прочитать или записать свойство, для которого соответствующая процедура была помечена атрибутом <xref:System.ObsoleteAttribute>; в этой ситуации компилятор выдает предупреждение.  
  
 Вы можете пометить любой программный элемент как неиспользуемый, применив к нему атрибут <xref:System.ObsoleteAttribute>. Если вы это сделаете, вы можете задать для свойства <xref:System.ObsoleteAttribute.IsError%2A> атрибута значение `True` или `False`. Если задать значение `True`, компилятор будет рассматривать попытку использовать элемент как ошибку. Если задать значение `False` или оставить значение по умолчанию `False`, то при попытке использовать элемент компилятор выдаст предупреждение.  
  
 По умолчанию это сообщение считается предупреждением, так как свойство <xref:System.ObsoleteAttribute.IsError%2A><xref:System.ObsoleteAttribute> имеет значение `False`. Дополнительные сведения о скрытии предупреждений и обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40019  
  
### Исправление ошибки  
  
1.  Проверьте указанное сообщение об ошибке и выполните соответствующее действие.  
  
2.  Убедитесь, что имя свойства в исходном коде написано правильно.  
  
3.  Избегайте доступа к свойству способом \(чтение или запись\), который приводит к возникновению этого сообщения.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)