---
title: "Разрешение вопросов, связанных с исключениями: System.Data.ConstraintException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ConstraintException - класс"
ms.assetid: 5e9ba3b8-73d5-4657-a76e-63ab6ea32cf1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Data.ConstraintException
Исключение <xref:System.Data.ConstraintException> вызывается при попытке выполнить действие, нарушающее ограничение.  
  
## Полезные советы  
 **Ослабьте или отключите ограничения в наборах данных**.  
 Можно использовать свойство <xref:System.Data.DataSet.EnforceConstraints%2A> для временного отключения ограничений при заполнении таблиц объекта <xref:System.Data.DataSet>.  
  
 **Убедитесь, что не пытаетесь присвоить значение полю первичного ключа, которое уже существует в таблице данных.**  
 Если первичный ключ существует, вызывается это исключение.  
  
 **Очистите наборы данных перед их загрузкой из состояния представления.**  
 Если в наборе данных при загрузке есть данные, может быть вызвано это исключение.  
  
## См. также  
 <xref:System.Data.ConstraintException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)