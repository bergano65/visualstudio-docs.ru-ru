---
title: "Пользовательская версия System.Runtime.CompilerServices.ExtensionAttribute, найденная компилятором, является недопустимой. | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36558"
  - "bc36558"
helpviewer_keywords: 
  - "BC36558"
ms.assetid: f47d310a-95fd-4340-bda2-21262c217dbb
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Пользовательская версия System.Runtime.CompilerServices.ExtensionAttribute, найденная компилятором, является недопустимой.
Пользовательская версия System.Runtime.CompilerServices.ExtensionAttribute найденная компилятором, является недопустимой. Для разрешения сборок, классов и методов должны быть установлены его флаги использования атрибута.  
  
 В пользовательской версии <xref:System.Runtime.CompilerServices.ExtensionAttribute?displayProperty=fullName>, обнаруженной компилятором, не устанавливаются флаги использования атрибута, чтобы разрешить применение атрибута к сборкам, методам и классам. Требуется применение по крайней мере к этим трем программным элементам.  
  
 **Идентификатор ошибки:** BC36558  
  
### Исправление ошибки  
  
-   Измените определение атрибута, чтобы включить применение этого атрибута по крайней мере к сборкам, методам и классам, как показано в следующих примерах.  
  
-   Используйте <xref:System.Runtime.CompilerServices.ExtensionAttribute?displayProperty=fullName> вместо пользовательской версии.  
  
## Пример  
 В следующем примере атрибут `AttributeUsage` используется для указания, к каким программным элементам можно применять новую версию `ExtensionAttribute`. В примере задаются три члена перечисления `AttributeTargets`: `Assembly`, `Class` и `Method`. Если пропустить любой из этих элементов, возникнет ошибка.  
  
```  
Namespace System.Runtime.CompilerServices <AttributeUsage(AttributeTargets.Assembly Or _ AttributeTargets.Class Or AttributeTargets.Method)> Class ExtensionAttribute Inherits System.Attribute ' Definitions of methods, fields, and properties. End Class End Namespace  
```  
  
 Кроме того, можно разрешить применение `ExtensionAttribute` ко всем программным элементам с помощью члена `All``AttributeTargets`.  
  
```  
<AttributeUsage(AttributeTargets.All)>  
```  
  
 Удаление строки `AttributeUsage`, как показано в следующем коде, дает тот же результат.  
  
```  
Namespace System.Runtime.CompilerServices Class ExtensionAttribute Inherits System.Attribute ' Definitions of methods, fields, and properties. End Class End Namespace  
```  
  
## См. также  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [НЕ В СБОРКЕ. обзор атрибутов в Visual Basic](http://msdn.microsoft.com/ru-ru/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [НЕ В СБОРКЕ. Настраиваемые атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/d72d8a5c-8f64-4614-b15b-cad66845d047)   
 [Методы расширения](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [НЕ В СБОРКЕ. Практическое руководство. Определение собственных атрибутов](http://msdn.microsoft.com/ru-ru/039609c4-ec43-4f44-945f-aa3b5b535c6a)   
 [Написание настраиваемых атрибутов](../Topic/Writing%20Custom%20Attributes.md)