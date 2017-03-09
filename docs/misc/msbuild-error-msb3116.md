---
title: "Ошибка MSBuild MSB3116 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.HostInBrowserNotOnlineOnly"
helpviewer_keywords: 
  - "MSB3116"
ms.assetid: bf04c587-d0e2-4d68-bbff-da9a985ea70e
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3116
**MSB3116: Приложение помечено для размещения в браузере, но оно помечено также и для сетевого и автономного использования.  Измените настройку приложения только на сетевое использование.**  
  
 При развертывании WPF\-приложения веб\-браузера необходимо задать для свойства <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> значение `True`.  Когда для свойства <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> задано значение `True`, необходимо задать для свойства <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A> значение `False` \(чтобы выполнение установки было доступно только из сети\).  Если последнее условие не соблюдено, появится данное сообщение об ошибке.  
  
### Чтобы исправить эту ошибку  
  
-   Задайте для свойства <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A> значение `False`.  
  
## См. также  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A>   
 [Страница публикации в конструкторе проектов](../ide/reference/publish-page-project-designer.md)