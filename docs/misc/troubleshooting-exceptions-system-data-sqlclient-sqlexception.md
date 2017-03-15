---
title: "Разрешение вопросов, связанных с исключениями: System.Data.SqlClient.SqlException | Microsoft Docs"
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
  - "SqlException - класс"
ms.assetid: 05f63457-3825-4541-ae09-0c771eb5ba35
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Data.SqlClient.SqlException
Исключение <xref:System.Data.SqlClient.SqlException> возникает при возврате SQL Server предупреждения или ошибки.  
  
## Полезные советы  
 **Убедитесь, что при подключении вы используете допустимые учетные данные.**  
 Убедитесь, что указанные учетные данные допустимы. Для получения дополнительной информации см. [How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md).  
  
 **Убедитесь, что имя сервера указано правильно и что он работает.**  
 Убедитесь, что используется правильное имя сервера и он доступен.  
  
### Примечания  
 Это исключение вызывается всякий раз при обнаружении сформированной сервером ошибки поставщиком данных .NET Framework для SQL Server.  
  
 Сообщения с уровнем важности 10 и менее являются информационными и обозначают неполадки, вызванные ошибками во введенных пользователем данных. Уровни важности с 11 по 16 создаются пользователем и могут быть исправлены им же. Уровни важности с 17 по 25 указывают на ошибки программного обеспечения или оборудования. При возникновении ошибок с уровнями 17,18 и 19 можно продолжать работу, хотя выполнение отдельных инструкций может оказаться невозможным.  
  
 <xref:System.Data.SqlClient.SqlConnection> остается открытым, если уровень важности не превышает 19. Когда уровень важности превышает 20, сервер обычно закрывает <xref:System.Data.SqlClient.SqlConnection>. Тем не менее, пользователь может опять открыть подключение и продолжить работу. В обоих случаях выполняющим команду методом создается <xref:System.Data.SqlClient.SqlException>.  
  
 Дополнительные сведения о посылаемых SQL Server предупреждениях и информационных сообщениях см. в разделе "Устранение неполадок" в электронной документации по SQL Server.  
  
## См. также  
 <xref:System.Data.SqlClient.SqlException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md)