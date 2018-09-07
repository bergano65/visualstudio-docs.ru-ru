---
title: Свойства MSBuild, поддерживаемые SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1695a23ba9dddc27a37f23c714678fe6b779d328
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674394"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Свойства MsBuild, поддерживаемые в SharePoint
  Любой [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] свойство, определенное в файле Microsoft.VisualStudio.SharePoint.targets, файле проекта или файле пользователя проекта может использоваться в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] проектов SharePoint. Помимо общих [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] свойства проекта, SharePoint определяет дополнительные свойства, характерные для проектов SharePoint.  
  
 Список общих [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] свойства, см. в разделе [общие свойства проектов MSBuild](http://go.microsoft.com/fwlink/?LinkID=168687). Полный список свойств, поддерживаемых языком программирования, см. *.targets* файл, файл проекта (*.csproj* или *.vbproj*), или пользователь project файла ( *csproj.user* или *. vbproj.user*).  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>Свойства MsBuild, относящиеся к SharePoint
 В следующей таблице перечислены [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] свойства, применяемые к проектов SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Существуют другие свойства, но они предназначены для внутреннего использования.  
  
|Имя свойства|Описание|  
|-------------------|-----------------|  
|SharePointSiteUrl|Строка, представляющая [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] на сайте SharePoint.|  
|SandboxedSolution|Логическое значение, указывающее, находится ли решение изолированное решение.|  
|ActiveDeploymentConfiguration|Активную конфигурацию развертывания.|  
|IncludeAssemblyInPackage|Логическое значение, указывающее, включаются ли сборки в файле пакета.|  
|PreDeploymentCommand|Строковое значение, представляющее команду для выполнения команды до развертывания.|  
|PostDeploymentCommand|Строковое значение, представляющее команду для выполнения команды после развертывания.|  
|CustomBeforeSharePointTargets|Строка, представляющая путь к [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] файл целевых объектов. Если файл целевых объектов существует и определен, он импортируется перед данными целевых объектов SharePoint. Это свойство позволяет настраивать процесс с предопределения свойства, связанные с упаковкой без изменения поставки файла целевых объектов SharePoint, пока файл целевых объектов по-прежнему применяется ко всем проектам SharePoint.|  
|CustomAfterSharePointTargets|Строка, представляющая путь к [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] файл целевых объектов. Если файл целевых объектов существует и определен, он импортируется в конце концов данных целевых объектов SharePoint. Это свойство позволяет настраивать процесс путем переопределения свойства, связанные с упаковкой и целевые объекты без необходимости изменения поставки файла целевых объектов SharePoint, пока файл целевых объектов по-прежнему применяется ко всем проектам SharePoint.|  
|LayoutPath|Строка, представляющая корневой каталог, куда каждого из файлов для упаковки временно помещаются перед добавлением к *.wsp* файл. Этот путь может быть полезно знать при переопределении целевых объектов BeforeLayout и AfterLayout для добавления, удаления или изменения файлов для упаковки, поскольку его можно использовать для изменения содержимого *.wsp* файл.|  
|BasePackagePath|Строка, представляющая папку, в которой размещается пакет. Это значение используется в выходной каталог проекта, например Bin\Debug.|  
|PackageExtension|Строка, представляющая расширение имени файла для добавления в пакет. Значение по умолчанию — wsp.|  
|AssemblyDeploymentTarget|Строка, представляющая расположение, расположение развертывания сборки проекта на сервере SharePoint. Значением является GlobalAssemblyCache (по умолчанию) или веб-приложения. Это свойство можно также задать в окне «Свойства».|  
|PackageWithValidation|Логическое значение, указывающее, выполняется ли проверка перед упаковкой. Это свойство позволяет игнорировать ошибки проверки при построении пакетов.|  
|ValidatePackageDependsOn|Строка, определяющая дополнительные цели для выполнения перед целью ValidatePackage.|  
|TokenReplacementFileExensions|Строка, которая определяет файлы, их токены заменяются во время упаковки.|  
  
## <a name="use-msbuild-properties-in-the-properties-page"></a>Использование свойств MsBuild на странице свойств
 Для обеспечения гибкости, вместо использования жестко запрограммированных строк в **Командная строка до развертывания** и **строка команды после развертывания** полях на странице свойств SharePoint, можно использовать SharePoint свойства в качестве аргументов. Например, вместо указания определенной [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] строку для сайта SharePoint, можно вместо этого использовать `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Можно использовать либо [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] синтаксис переменной `$(` *propertyName* `)` или синтаксис переменной среды `%` *propertyName* `%` Чтобы задать свойство.  
  
## <a name="see-also"></a>См. также
 [Справочные сведения о MSBuild](/visualstudio/msbuild/msbuild-reference)  
  