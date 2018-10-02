---
title: С помощью MSBuild | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8b776823c78835ad687a110c1fcc0ba1382bead
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559668"
---
# <a name="using-msbuild"></a>Использование MSBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [использование MSBuild](https://docs.microsoft.com/visualstudio/extensibility/internals/using-msbuild).  
  
MSBuild предоставляет строго определенными, расширяемый формат XML для создания файлов проекта, полного описания элементов проекта для построения, задачи сборки и конфигураций сборки.  
  
 Пример end-to-end языка системы проекта, основанные на MSBuild, см. в разделе Пример IronPython, глубокое погружение в[примеры VSSDK](../../misc/vssdk-samples.md).  
  
## <a name="general-msbuild-considerations"></a>MSBuild общие вопросы  
 Файлы проекта MSBuild, например, [!INCLUDE[csprcs](../../includes/csprcs-md.md)] .csproj и [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] файлы .vbproj, содержат данные, которые используются во время сборки, но также может содержать данные, которые используются во время разработки. Во время сборки данные хранятся с помощью MSBuild примитивов, включая [элемент Item (MSBuild)](../../msbuild/item-element-msbuild.md) и [элемент Property (MSBuild)](../../msbuild/property-element-msbuild.md). Данные времени разработки, то данные, относящиеся к данного типа проектов и любых подтипов связанный проект, хранятся в XML произвольной формы, зарезервированного для ее.  
  
 MSBuild не имеют встроенной поддержки для объектов конфигурации, но поддерживает условные атрибуты для указания данных конфигурации. Пример:  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Дополнительные сведения о условные атрибуты, см. в разделе [условных конструкциях](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Расширение для данного типа проекта MSBuild  
 MSBuild интерфейсы и интерфейсы API могут быть изменены в будущих версиях [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Таким образом разумно использовать классы управляемых пакетов framework (MPF), поскольку они обеспечивают защиту от изменений.  
  
 Managed Package Framework для проектов (MPFProj) предоставляет вспомогательные классы для создания и управления новую систему проектов. Источник кода и компиляция инструкции доступны в [MPF для проектов — Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Ниже приведены классы MPF конкретного проекта.  
  
|Класс|Реализация|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` класс является оболочкой для элементов MSBuild.  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>Vs генераторов одного файла. Задачи MSBuild  
 Один файл генераторы доступ-только во время разработки, но задачи MSBuild можно использовать во время разработки и во время сборки. Для обеспечения максимальной гибкости поэтому используйте задачи MSBuild для преобразования и создания кода. Дополнительные сведения см. в разделе [средства пользовательских](../../extensibility/internals/custom-tools.md).  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о MSBuild](../../msbuild/msbuild-reference.md)   
 [MSBuild](http://msdn.microsoft.com/en-us/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [Настраиваемые средства](../../extensibility/internals/custom-tools.md)

