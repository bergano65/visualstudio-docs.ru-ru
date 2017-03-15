---
title: "Разрешение вопросов, связанных с исключениями: System.Deployment.Application.InvalidDeploymentException | Microsoft Docs"
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
  - "InvalidDeploymentException - класс"
ms.assetid: 4361e053-8eaf-44e3-b8ac-95516d8d1832
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Deployment.Application.InvalidDeploymentException
Исключение <xref:System.Deployment.Application.InvalidDeploymentException> вызывается, когда приложение или манифесты \(приложения и развертывания\) недопустимы.  
  
## Полезные советы  
 **Убедитесь в действительности манифестов для этого приложения.**  
 Манифест приложения — это файл XML, который описывает и определяет общие и закрытые сборки одновременного выполнения, которые приложению следует подключить во время выполнения. Это должны быть те же версии сборок, что и использованные для проверки приложения. Манифесты приложения также могут описывать метаданные закрытых для приложения файлов.  
  
 **Используйте функцию ClickOnce для развертывания приложения.**  
 Используйте функцию ClickOnce для упрощения установки — публикации приложений Windows на веб–сервер или общий сетевой ресурс. Для получения дополнительной информации см. [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
## См. также  
 <xref:System.Deployment.Application.InvalidDeploymentException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Устранение неполадок развертывания ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [ClickOnce Deployment for Windows Forms](../Topic/ClickOnce%20Deployment%20for%20Windows%20Forms.md)