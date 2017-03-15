---
title: "Ошибка MSBuild MSB3185 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.NoEntryPoint"
helpviewer_keywords: 
  - "MSB3185"
ms.assetid: 032c63c5-d662-42ba-84e1-e3ccca8cee05
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3185
**MSB3185: для манифеста не указана точка входа.**  
  
 Эта ошибка возникает в случае, когда для манифеста не указывается точка входа.  Такая ошибка может быть связана как с манифестом приложения, так и с манифестом развертывания.  
  
### Чтобы исправить эту ошибку  
  
-   Если используется задача GenerateApplicationManifest, то убедитесь в том, что указана допустимая точка входа или задайте для свойства TargetFrameworkVersion значение "v3.5" или более высокое.  Для манифеста приложения допустимой точкой входа является EXE–файл.  
  
-   Если используется задача GenerateDeploymentManifest , то убедитесь в том, что в манифестах указаны допустимые точки входа.  Для манифеста развертывания допустимой точкой входа является манифест приложения.  
  
## См. также  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [Страница публикации в конструкторе проектов](../ide/reference/publish-page-project-designer.md)   
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)   
 [Ошибка MSBuild MSB3116](../misc/msbuild-error-msb3116.md)   
 [Ошибка MSBuild MSB3117](/visual-cpp/misc/msbuild-error-msb3117)   
 [Ошибка MSBuild MSB3118](../misc/msbuild-error-msb3118.md)   
 [Ошибка MSBuild MSB3174](/visual-cpp/misc/msbuild-error-msb3174)