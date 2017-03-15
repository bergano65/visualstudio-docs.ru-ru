---
title: "Разрешение вопросов, связанных с исключениями: System.Net.CookieException | Microsoft Docs"
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
  - "CookieException - класс"
ms.assetid: 7db6b962-cc5e-4b63-be65-894a8f186b38
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Net.CookieException
Исключение <xref:System.Net.CookieException> возникает при ошибке при добавлении файла cookie в контейнер.  
  
## Полезные советы  
 **Убедитесь, что размер файла cookie не превышает максимальное значение, допустимое контейнером файлов cookie.**  
 Это исключение возникает, если предпринимается попытка добавить в <xref:System.Net.Cookie> объект <xref:System.Net.CookieContainer.MaxCookieSize%2A> с длиной большей, чем <xref:System.Net.CookieContainer>. По умолчанию, максимальный размер файла cookie равен 4 096 байт.  
  
 **При задании свойства имени для файла cookie убедитесь, что значение не является пустой ссылкой или пустой строкой.**  
 Свойство <xref:System.Net.Cookie.Name%2A> должно инициализироваться до использования экземпляра класса <xref:System.Net.Cookie>. Следующие знаки зарезервированы и не могут использоваться для этого значения атрибута: знак равенства, точка с запятой, запятая, последовательность знаков перехода на новую строку \(\\n\), возврат каретки \(\\r\), табуляция \(\\t\). Знак доллара \($\) не может быть первым знаком.  
  
 **При установке свойства порта файла cookie убедитесь, что значение является допустимым и заключено в двойные кавычки.**  
 Атрибут <xref:System.Net.Cookie.Port%2A> ограничивает порты, на которые может посылаться данный файл cookie. По умолчанию ограничения не устанавливаются. Установка свойства равным пустой строке \(""\) ограничивает диапазон портов до того одного, который используется в HTTP\-ответе. В противном случае значение должно быть строкой в кавычках, которая содержит значения портов, разделенные запятыми.  
  
 **При задании свойства "Значение" файла cookie, убедитесь, что значение отлично от значения NULL.**  
 Следующие символы зарезервированы и не могут быть использованы в значении этого свойства: точка с запятой, запятая.  
  
## См. также  
 <xref:System.Net.CookieException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Write a Cookie](../Topic/How%20to:%20Write%20a%20Cookie.md)