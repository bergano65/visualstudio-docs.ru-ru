---
title: "Разрешение вопросов, связанных с исключениями: Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CantStartSingleInstanceException - исключение"
  - "Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException - исключение"
ms.assetid: 3639f15d-9547-43da-8145-60da34782991
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException
Исключение вызывается, когда второй экземпляр приложения с одним экземпляром не может подключиться к первому экземпляру.  
  
## Примечания  
 Возможными причинами этой ошибки могут быть:  
  
-   Исходный экземпляр перестал отвечать.  
  
-   Приложение не имеет разрешений на создание объектов ядра.  
  
     Базовое имя для объектов ядра получается из последовательного объединения GUID сборки, основного номера версии и дополнительного номера версии. Например, базовое имя может быть 3639f15d\-9547\-43da\-8145\-60da347829915.1.  
  
## См. также  
 <xref:Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)