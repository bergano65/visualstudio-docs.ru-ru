---
title: "Свойства MSBuild, поддерживаемые в SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, MSBuild properties
ms.assetid: 7b2b58c6-55cd-4682-a5d7-43874e70920d
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: af70078790c684ce774a203b265d7c767779ab15
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Свойства MSBuild, поддерживаемые в проектах SharePoint
  Любой [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] свойство, определенное в файле Microsoft.VisualStudio.SharePoint.targets, файл проекта или пользовательского файла проекта можно использовать в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] проектов SharePoint. В дополнение к общим [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] свойства, предоставленные в проекте SharePoint определяет дополнительные свойства, характерные для проектов SharePoint.  
  
 Список общих [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] свойствах см. [общие свойства проектов MSBuild](http://go.microsoft.com/fwlink/?LinkID=168687). Полный список свойств, поддерживаемых языком программирования, искать в TARGETS-файл, файл проекта (CSPROJ или VBPROJ) или пользовательского файла проекта (csproj.user или. vbproj.user).  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>Свойства MSBuild, характерные для SharePoint  
 В следующей таблице перечислены [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] свойств, применяемых для проектов SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Существуют другие свойства, но они предназначены для внутреннего использования.  
  
|Имя свойства|Описание:|  
|-------------------|-----------------|  
|SharePointSiteUrl|Строка, представляющая [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] на сайте SharePoint.|  
|SandboxedSolution|Логическое значение, указывающее, является ли решение изолированное решение.|  
|ActiveDeploymentConfiguration|Активной конфигурации развертывания.|  
|IncludeAssemblyInPackage|Логическое значение, указывающее, включаются ли сборки в файле пакета.|  
|PreDeploymentCommand|Строковое значение, представляющее команду для выполнения перед развертыванием.|  
|PostDeploymentCommand|Строковое значение, представляющее команду для выполнения после развертывания.|  
|CustomBeforeSharePointTargets|Строка, представляющая путь [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] файл целевых объектов. Если целевой файл существует и определен, он импортируется перед данными целевых объектов SharePoint. Это свойство позволяет настраивать процесс посредством предопределения свойств, связанных с упаковкой без изменения поставки файла целевых объектов SharePoint, пока файл целевых объектов по-прежнему применяется ко всем проектам SharePoint.|  
|CustomAfterSharePointTargets|Строка, представляющая путь [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] файл целевых объектов. Если целевой файл существует и определен, он импортируется после того как все данные целевых объектов SharePoint. Это свойство позволяет настраивать процесс путем переопределения свойств, связанных с упаковкой и целевых объектов без необходимости изменения поставки файла целевых объектов SharePoint, пока файл целевых объектов по-прежнему применяется ко всем проектам SharePoint.|  
|LayoutPath|Строка, представляющая корневой каталог, где всех файлов, упаковываемых временно располагаются перед добавлением в WSP-файл. Этот путь может быть полезно знать при переопределении целевых объектов BeforeLayout и AfterLayout для добавления, удаления или изменения файлов для упаковки, так как его можно использовать для изменения содержимого WSP-файла.|  
|BasePackagePath|Строка, представляющая папку, в которой размещается пакет. Это значение использует выходной каталог проекта, например Bin\Debug.|  
|PackageExtension|Строка, представляющая расширение имени файла для добавления в пакет. Значение по умолчанию — WSP-файла.|  
|AssemblyDeploymentTarget|Строка, представляющая расположение, где развернута сборка проекта на сервере SharePoint. Значением является GlobalAssemblyCache (по умолчанию) или веб-приложения. Это свойство можно также задать в окне «Свойства».|  
|PackageWithValidation|Логическое значение, указывающее, выполняется ли проверка перед упаковкой. Это свойство позволяет игнорировать ошибки проверки при построении пакетов.|  
|ValidatePackageDependsOn|Строка, определяющая дополнительные цели для выполнения перед целью ValidatePackage.|  
|TokenReplacementFileExensions|Строка, определяющая файлы, токены заменяются во время упаковки.|  
  
## <a name="using-msbuild-properties-in-the-properties-page"></a>С помощью свойства MSBuild на странице свойств  
 Для обеспечения гибкости, вместо использования жестко запрограммированных строк в **строка команды до развертывания** и **командной строки после развертывания** поля на странице свойств SharePoint можно использовать SharePoint свойства в качестве аргументов. Например, вместо указания определенной [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] строка для сайта SharePoint, можно вместо этого использовать `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Можно использовать любой [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] синтаксис переменной `$(` *propertyName* `)` или синтаксис переменной среды `%` *propertyName* `%` Чтобы задать свойство.  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о MSBuild](/visualstudio/msbuild/msbuild-reference)  
  
  