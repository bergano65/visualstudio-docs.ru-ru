---
title: "Ошибка MSBuild MSB3118 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.UseApplicationTrustInvalidFrameworkVersion"
helpviewer_keywords: 
  - "MSB3118"
ms.assetid: 9bf5b430-0cfb-4da5-a7f7-04d69f20cce1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3118
**MSB3118: приложение задано для использования доверия приложения, однако TargetFrameworkVersion не является версией v3.5.**  
  
 Это сообщение появляется, когда для свойства <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.UseApplicationTrust%2A> задается значение `True`, а для свойства <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> задается версия ниже `v3.5` \(например `v2.0`\).  
  
### Чтобы исправить эту ошибку  
  
-   Задайте для свойства <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> значение `v3.5` или более позднюю версию.  
  
## См. также  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.UseApplicationTrust%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.UseApplicationTrust%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 [Страница публикации в конструкторе проектов](../ide/reference/publish-page-project-designer.md)   
 [Ошибка MSBuild MSB3116](../misc/msbuild-error-msb3116.md)   
 [Ошибка MSBuild MSB3117](/visual-cpp/misc/msbuild-error-msb3117)   
 [Ошибка MSBuild MSB3119](../misc/msbuild-error-msb3119.md)   
 [Ошибка MSBuild MSB3174](/visual-cpp/misc/msbuild-error-msb3174)   
 [Ошибка MSBuild MSB3185](../misc/msbuild-error-msb3185.md)