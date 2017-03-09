---
title: "Значение ConnectionTimeout должно быть больше 0. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrNetwork_BadConnectionTimeout"
ms.assetid: 15ac09a7-47f0-44f3-9e84-5bd10bd07450
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Значение ConnectionTimeout должно быть больше 0.
При отправке и загрузке файлов с помощью [Объект My.Computer.Network](/dotnet/visual-basic/language-reference/objects/my-computer-network-object) необходимо указать `connectionTimeout` больше `0`.  
  
### Исправление ошибки  
  
-   Укажите `connectionTimeout` больше `0`.  
  
## См. также  
 [Метод My.Computer.Network.UploadFile](http://msdn.microsoft.com/ru-ru/5505ea3e-3dbd-460b-9f8f-62c84c0a4de6)   
 [Метод My.Computer.Network.DownloadFile](http://msdn.microsoft.com/ru-ru/aeb7ed8f-1ac9-4242-ae57-9f35914eb329)   
 [Практическое руководство. Выгрузка файла](../Topic/How%20to:%20Upload%20a%20File%20in%20Visual%20Basic.md)   
 [Практическое руководство. Загрузка файла](../Topic/How%20to:%20Download%20a%20File%20in%20Visual%20Basic.md)   
 [Сетевые операции в .NET Framework с Visual Basic](http://msdn.microsoft.com/ru-ru/c5379021-44ef-4d6a-acf5-e951fdcab6b2)