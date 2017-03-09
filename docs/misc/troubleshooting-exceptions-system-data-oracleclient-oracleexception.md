---
title: "Разрешение вопросов, связанных с исключениями: System.Data.OracleClient.OracleException | Microsoft Docs"
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
  - "OracleException - класс"
  - "Oracle"
  - "исключения, Oracle"
ms.assetid: 08b9206e-baa9-4caa-b0c7-ece2118f6e2d
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Data.OracleClient.OracleException
Исключение <xref:System.Data.OracleClient.OracleException> возникает, когда база данных Oracle или поставщик данных .NET Framework для Oracle возвращает предупреждение или ошибку.  
  
## Полезные советы  
 **Убедитесь, что при подключении вы используете допустимые учетные данные.**  
 Убедитесь, что указанные учетные данные допустимы.  
  
 **Убедитесь, что имя сервера указано правильно и что он работает.**  
 Убедитесь, что используется правильное имя сервера и он доступен.  
  
## Заметки  
 Это исключение возникает всякий раз, когда <xref:System.Data.OracleClient.OracleDataAdapter> встречает ошибку, сформированную сервером.  
  
 В случае серьезной ошибки сервер может закрыть объект <xref:System.Data.OracleClient.OracleConnection>. Тем не менее, пользователь может опять открыть подключение и продолжить работу.  
  
## См. также  
 <xref:System.Data.OracleClient.OracleException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)