---
title: "Использование MSBuild | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3b9d05b85cacfcdf90a883ffd08d4dec316eaafc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="using-msbuild"></a>С помощью MSBuild
MSBuild предоставляет строго определенными, расширяемый формат XML для создания файлов проекта, которые полностью описать элементы проекта для построения, построение задач и конфигураций сборки.  
  
## <a name="general-msbuild-considerations"></a>MSBuild общие вопросы  
 Файлы проекта MSBuild, например, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .vbproj файлы, содержащие данные, используется во время построения, но может также содержать данные, используемые во время разработки. Во время построения данные хранятся с использованием MSBuild примитивные типы, включая [элемент Item (MSBuild)](../../msbuild/item-element-msbuild.md) и [элемент Property (MSBuild)](../../msbuild/property-element-msbuild.md). Данные во время разработки, то есть данные, специфичные для данного типа проектов и любых подтипов связанный проект, хранится в произвольной формы XML, зарезервированы для него.  
  
 MSBuild не имеет встроенную поддержку объектов конфигурации, но корпорация Майкрософт предоставляет условные атрибуты для указания данных конфигурации. Пример:  
  
```xml  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Дополнительные сведения о условные атрибуты см. в разделе [условной конструкции](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Расширение для данного типа проекта MSBuild  
 Интерфейсы MSBuild и API-интерфейсы могут быть изменены в будущих версиях [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Таким образом рекомендуется использовать классы managed package framework (MPF), так как он обеспечивает защиту от изменений.  
  
 Managed Package Framework для проектов (MPFProj) предоставляет вспомогательные классы для создания и управления новую систему проектов. Найти источник кода и компиляция инструкции в [MPF для проектов - Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Ниже приведены классы MPF для конкретного проекта.  
  
|Класс|Реализация|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement`класс является оболочкой для элементов MSBuild.  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>Генераторы одиночных файлов vs. Задачи MSBuild  
 Один файл генераторы доступны-только во время разработки, но задачи MSBuild, которые могут использоваться во время разработки и во время построения. Для обеспечения максимальной гибкости таким образом, используйте задачи MSBuild для преобразования и создания кода. Дополнительные сведения см. в разделе [средства пользовательских](../../extensibility/internals/custom-tools.md).  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о MSBuild](../../msbuild/msbuild-reference.md)   
 [MSBuild](../../msbuild/msbuild.md)   
 [Настраиваемые средства](../../extensibility/internals/custom-tools.md)