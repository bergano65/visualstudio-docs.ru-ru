---
title: "Разрешение вопросов, связанных с исключениями: System.Exception | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Exception - исключение"
  - "базовые классы, исключения"
  - "исключения, базовый класс"
ms.assetid: fc15931a-9323-47c6-a42f-55d0534b939a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Exception
Представляет ошибки, происходящие во время выполнения приложения. Этот класс является базовым классом для всех исключений.  
  
## Полезные советы  
 **Для получения дополнительных сведений проверьте свойство InnerException.**  
 Чтобы устранить ошибку, возможно потребуется информация о внутреннем \(или предыдущем\) исключении, которое привело к текущему исключению. Свойство <xref:System.Exception.InnerException%2A> текущего исключения содержит внутреннее исключение. Можно использовать ссылку **Показать подробно** в диалоговом окне **Помощник исключения** для доступа к свойству <xref:System.Exception.InnerException%2A>.  
  
 **Временно отключите "Отлаживать только мой код".**  
 Исключение, возможно, возникло в коде, который писали не вы. Чтобы отладить этот код, следует выключить опцию "Отлаживать только мой код" Для получения дополнительной информации см. [Страница "Общие", папка "Отладка", диалоговое окно "Параметры"](../debugger/general-debugging-options-dialog-box.md).  
  
## См. также  
 <xref:System.Exception>   
 <xref:System.Exception.InnerException%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Практическое руководство. Прерывание выполнения при создании исключения](../misc/how-to-break-when-an-exception-is-thrown.md)   
 [Страница "Общие", папка "Отладка", диалоговое окно "Параметры"](../debugger/general-debugging-options-dialog-box.md)