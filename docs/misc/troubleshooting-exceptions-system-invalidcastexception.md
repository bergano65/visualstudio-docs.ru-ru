---
title: "Разрешение вопросов, связанных с исключениями: System.InvalidCastException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "InvalidCastException - класс"
ms.assetid: a855dfe1-5c06-45a6-9c2f-c9e799ccf8f0
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.InvalidCastException
Исключение <xref:System.InvalidCastException> порождается при возникновении сбоя во время преобразования явной ссылки. Ссылки преобразования преобразовывают из одного ссылочного типа в другой. Они могут изменить тип ссылки, но они никогда не изменяют тип или значение элемента, на который указывает ссылка. Приведение объектов из одного типа в другой часто является причиной возникновения этого исключения.  
  
## Полезные советы  
 **Проверьте назначение исходного типа с конечным типами, чтобы убедиться, что преобразование является допустимым.**  
 Сведения о преобразованиях, поддерживаемых системой, см. в <xref:System.Convert>.  
  
## Примечания  
 При успешном явном преобразовании ссылки, исходным значением должно быть Null \(`Nothing`в Visual Basic\), или тип объекта, вызванного с помощью исходного аргумента, должен быть конвертируемым в конечный тип с помощью неявного преобразования ссылки.  
  
 При обновлении Visual Basic до новой версии и запуска приложения Visual Basic 6.0 с вызовом пользовательского события в элементе управления пользователя, может возникнуть исключение, сообщающее, что указанное приведение неверно. Чтобы устранить эту ошибку, найдите следующую строку кода в  `Form1`:  
  
 `Call UserControl11_MyCustomEvent(UserControl11, New UserControl1.MyCustomEventEventArgs(5))`  
  
 И замените ее на:  
  
 `Call UserControl11_MyCustomEvent(UserControl11(0), New UserControl1.MyCustomEventEventArgs(5))`  
  
## См. также  
 <xref:System.InvalidCastException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Практическое руководство. Преобразование объекта к другому типу в Visual Basic](../Topic/How%20to:%20Convert%20an%20Object%20to%20Another%20Type%20in%20Visual%20Basic.md)   
 [Преобразование строк в типы данных .NET Framework](../Topic/Converting%20Strings%20to%20.NET%20Framework%20Data%20Types.md)   
 [Практическое руководство. Реализация определенных пользователем преобразований между структурами](../Topic/How%20to:%20Implement%20User-Defined%20Conversions%20Between%20Structs%20\(C%23%20Programming%20Guide\).md)