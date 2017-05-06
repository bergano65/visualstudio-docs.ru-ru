---
title: "Свойства MSBuild, поддерживаемые в проектах SharePoint"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "разработка приложений SharePoint в Visual Studio, свойства MSBuild"
ms.assetid: 7b2b58c6-55cd-4682-a5d7-43874e70920d
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Свойства MSBuild, поддерживаемые в проектах SharePoint
  Любое свойство [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)], определенное в файле Microsoft.VisualStudio.SharePoint.targets, файле проекта или файле пользователя проекта, может быть использовано в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] проектах SharePoint.  В дополнение к общим свойствам [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] проекта, SharePoint определяет дополнительные свойства, специфические для проектов SharePoint.  
  
 Список стандартных свойств [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] см. в разделе [Общие свойства проектов MSBuild](http://go.microsoft.com/fwlink/?LinkID=168687).  Полный список свойств доступных в используемом языке программирования можно посмотреть в файле .targets, файле проекта \(.csproj или .vbproj\) или файле пользователя проекта \(csproj.user или .vbproj.user\).  
  
## Свойства MSBuild, специфические для проекта SharePoint  
 В следующей таблице перечислены свойства [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)], применяемые исключительно для проектов SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Другие свойства для внутреннего использования.  
  
|Имя свойства|Описание|  
|------------------|--------------|  
|SharePointSiteUrl|Строка, которая представляет [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] на сайте SharePoint.|  
|SandboxedSolution|Логическое значение, показывающее является ли решение обезвреженным.|  
|ActiveDeploymentConfiguration|Активная конфигурация развертывания.|  
|IncludeAssemblyInPackage|Логическое значение, которое позволяет определить, включена ли сборка в файл пакета.|  
|PreDeploymentCommand|Строковое значение, представляющее команду для выполнения перед развертыванием.|  
|PostDeploymentCommand|Строковое значение, представляющее команду для выполнения после развертывания.|  
|CustomBeforeSharePointTargets|Строка, представляющая путь файла целевых объектов [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)].  Если файл целевых объектов существует и определен, он импортируется перед любыми данными целевых объектов SharePoint.  Это свойство позволяет настраивать процесс упаковывания посредством предопределения свойств, относящихся к упаковыванию, без изменения поставки файла целевых объектов SharePoint, пока файл целевых объектов все еще применяется ко всем проектам SharePoint.|  
|CustomAfterSharePointTargets|Строка, представляющая путь файла целевых объектов [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)].  Если файл целевых объектов существует и определен, он импортируется после всех данных целевых объектов SharePoint.  Это свойство позволяет настраивать процесс упаковывания посредством переопределения свойств и целей, относящихся к упаковыванию, без изменения поставки файла целевых объектов SharePoint, пока файл целевых объектов все еще применяется ко всем проектам SharePoint.|  
|LayoutPath|Строка, представляющая корневой каталог, где каждый упаковываемый файл, перед добавлением, временно помещается в WPS\-файл.  Этот путь может быть полезен для понимания того, где переопределяются цели BeforeLayout и AfterLayout для добавления, удаления или изменения упаковываемых файлов, так как их можно использовать для изменения содержимого WPS\-файла.|  
|BasePackagePath|Строка, представляющая папку, в которой размещается пакет.  Это значение использует выходной каталог проекта, например, Bin\\Debug.|  
|PackageExtension|Строка, представляющая расширение имени файла, добавляемое к пакету.  Значением по умолчанию является wsp.|  
|AssemblyDeploymentTarget|Строка, представляющая местоположение, куда осуществляется развертывание сборки проекта на сервере SharePoint.  Она принимает значение GlobalAssemblyCache \(по умолчанию\) или WebApplication.  Это свойство может быть также задано в окне "Свойства".|  
|PackageWithValidation|Логическое значение, показывающее выполнена ли проверка перед упаковкой.  Это свойство позволяет игнорировать ошибки проверки при построении пакетов.|  
|ValidatePackageDependsOn|Строка, определяющая дополнительные цели для выполнения перед целью ValidatePackage.|  
|TokenReplacementFileExensions|Строка, определяющая файлы, токены которых были перемещены во время упаковки.|  
  
## Использование свойств MSBuild на странице свойств  
 Для гибкости, в полях **Командная строка: выполнение перед развертыванием** и **Командная строка: выполнение после развертывания** страницы свойств SharePoint, вместо использования жестко запрограммированных строк, в качестве аргументов можно использовать свойства SharePoint.  Например, вместо указания определенной строки [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] сайта SharePoint, можно использовать `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Чтобы задать свойство, можно воспользоваться синтаксисом переменной [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] `$(`*propertyName*`)` или синтаксисом переменной среды `%`*propertyName*`%`.  
  
## См. также  
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)  
  
  