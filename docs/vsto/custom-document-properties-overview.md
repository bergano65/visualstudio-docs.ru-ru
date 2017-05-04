---
title: "Общие сведения о настраиваемых свойствах документа | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "_AssemblyLocation - свойство"
  - "_AssemblyName - свойство"
  - "настраиваемые свойства документа"
  - "настройки уровня документа [разработка решений Office в Visual Studio], настраиваемые свойства"
  - "документы [разработка решений Office в Visual Studio], настраиваемые свойства"
  - "Office - документы [разработка решений Office в Visual Studio], настраиваемые свойства"
ms.assetid: 9a215904-b760-4a49-93e8-a1a708ce0526
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Общие сведения о настраиваемых свойствах документа
  При построении проекта уровня документа Visual Studio добавляет два настраиваемых свойства в документ проекта: \_AssemblyLocation и \_AssemblyName.  Когда пользователь открывает документ, приложение Microsoft Office осуществляет проверку настраиваемых свойств документа.  Если свойства уже указаны в документе, приложение загружает среду [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], которая запускает настройку.  Дополнительные сведения см. в разделе [Архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## \_AssemblyName  
 Это свойство содержит идентификатор CLSID интерфейса в компоненте загрузчика решения Office в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  Значение CLSID равно 4E3C66D5\-58D4\-491E\-A7D4\-64AF99AF6E8B.  Это значение не следует менять ни при каких обстоятельствах.  
  
## \_AssemblyLocation  
 Свойство содержит строку с указанием детальных данных манифеста развертывания для настройки.  Дополнительные сведения о манифестах см. в разделе [Манифесты приложения и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Способ развертывания решения определяет различные форматы значения свойства \_AssemblyLocation.  
  
-   Если решение публикуется для установки с веб\-узла, пути UNC, или с CD или USB диска, свойство \_AssemblyLocation имеет формат *DeploymentManifestPath*|*SolutionID*.  Примером служит следующая строка:  
  
     file:\/\/deployserver\/MyShare\/ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9  
  
-   Если вы запускаете или настраиваете решение в Visual Studio, свойство \_AssemblyLocation имеет формат *DeploymentManifestName*|*SolutionID*|vstolocal.  Примером служит следующая строка:  
  
     ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9|vstolocal  
  
 *SolutionID* — это GUID, который используется [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] для идентификации решения.  *SolutionID* автоматически создается при построении проекта. Термин **vstolocal** указывает на [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], что сборка должна быть загружена из одной папки в виде документа.  
  
## См. также  
 [Архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md)   
 [Манифесты приложения и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Практическое руководство. Публикация решения Office с помощью ClickOnce](http://msdn.microsoft.com/ru-ru/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Практическое руководство. Создание и изменение настраиваемых свойств документа](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  