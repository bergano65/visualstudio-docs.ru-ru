---
title: Использование MSBuild | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a1ad59e6d8f4cb88004629b0dfd2cdf0631a7824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297679"
---
# <a name="using-msbuild"></a>Использование MSBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

MSBuild предоставляет четко определенный расширяемый XML-формат для создания файлов проекта, которые полностью описывают элементы проекта для построения, задачи сборки и конфигурации сборки.  
  
 Полный пример системы проектного языка, основанной на MSBuild, см. в разделе[примеры VSSDK](../../misc/vssdk-samples.md).  
  
## <a name="general-msbuild-considerations"></a>Общие рекомендации по MSBuild  
 Файлы проекта MSBuild, например [!INCLUDE[csprcs](../../includes/csprcs-md.md)] . csproj и [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . vbproj, содержат данные, используемые во время сборки, но также могут содержать данные, используемые во время разработки. Данные времени сборки хранятся с помощью примитивов MSBuild, включая [элемент Item (MSBuild)](../../msbuild/item-element-msbuild.md) и [элемент Property (MSBuild)](../../msbuild/property-element-msbuild.md). Данные времени разработки, которые являются данными, относящимися к типу проекта и всем связанным подтипам проекта, хранятся в XML-файле произвольной формы, зарезервированном для него.  
  
 MSBuild не поддерживает встроенную поддержку объектов конфигурации, но предоставляет условные атрибуты для указания данных, относящихся к конфигурации. Пример:  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Дополнительные сведения об условных атрибутах см. в разделе [Условные конструкции](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Расширение MSBuild для типа проекта  
 Интерфейсы и API MSBuild могут быть изменены в будущих версиях [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Таким образом, разумно использовать классы Managed Package Framework (MPF), так как они обеспечивают экранирование от изменений.  
  
 Платформа управляемых пакетов для проектов (Мпфпрож) предоставляет вспомогательные классы для создания новой системы проектов и управления ею. Исходный код и инструкции по компиляции можно найти по адресу [MPF for Projects-Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
 Классы MPF, относящиеся к проекту, выглядят следующим образом:  
  
|Класс|Реализация|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` класс является оболочкой для элементов MSBuild.  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>Генераторы одиночных файлов и задачи MSBuild  
 Генераторы отдельных файлов доступны только во время разработки, но задачи MSBuild можно использовать во время разработки и во время сборки. Для максимальной гибкости, следовательно, используйте задачи MSBuild для преобразования и создания кода. Дополнительные сведения см. в разделе [Custom Tools](../../extensibility/internals/custom-tools.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по MSBuild](../../msbuild/msbuild-reference.md)   
 [MSBuild](https://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [Настраиваемые инструменты](../../extensibility/internals/custom-tools.md)
