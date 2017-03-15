---
title: "Разрешение вопросов, связанных с исключениями: System.Net.WebException | Microsoft Docs"
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
  - "WebException - класс"
ms.assetid: 6cd69a2c-c52b-420d-be47-a4e34eaec6f3
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Net.WebException
Исключение <xref:System.Net.WebException> вызывается, если ошибка возникает во время доступа к сети через подключаемый протокол.  
  
## Полезные советы  
 **Проверьте свойство Response исключения, чтобы определить причину сбоя запроса.**  
 При вызове <xref:System.Net.WebException> потомками класса <xref:System.Net.WebRequest> свойство <xref:System.Net.WebException.Response%2A> предоставляет приложению ответ Интернета.  
  
 **Проверьте свойство Status исключения, чтобы определить причину сбоя запроса.**  
 Свойство <xref:System.Net.WebException.Status%2A> исключения предоставляет сведения о состоянии для ошибки. Дополнительные сведения см. в разделе <xref:System.Net.WebExceptionStatus>.  
  
 **Если при входе в веб–службу XML истекает время ожидания, установите для времени ожидания при вызове веб–службы XML значение бесконечности.**  
 Для получения дополнительной информации см. [Ошибка: время ожидания при отладке веб\-служб](../debugger/error-timeout-while-debugging-web-services.md).  
  
## См. также  
 <xref:System.Net.WebException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Практическое руководство. Отправка данных с помощью класса WebRequest](../Topic/How%20to:%20Send%20Data%20Using%20the%20WebRequest%20Class.md)   
 [Практическое руководство. Запрос данных с помощью класса WebRequest](../Topic/How%20to:%20Request%20Data%20Using%20the%20WebRequest%20Class.md)   
 [Практическое руководство. Получение объекта WebResponse, соответствующего объекту WebRequest, для определенного протокола](../Topic/How%20to:%20Retrieve%20a%20Protocol-Specific%20WebResponse%20that%20Matches%20a%20WebRequest.md)