---
title: "С помощью MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Пакеты VSPackage, компиляция с MSBuild"
  - "MSBuild, расширяемость"
  - "пакеты, компиляция с MSBuild"
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# С помощью MSBuild
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

MSBuild предоставляет строго определенными, расширяемый формат XML для создания файлов проекта, которые полностью описать элементы проекта для построения, задачи построения и конфигураций построения.  
  
 Пример end\-to\-end языка системы проекта, в зависимости от MSBuild см. Образец IronPython глубокое погружение в[Примеры VSSDK](../../misc/vssdk-samples.md).  
  
## MSBuild общие вопросы  
 Файлы проекта MSBuild, например, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] файлы .vbproj, содержат данные, используемые во время построения, но также может содержать данные, используемые во время разработки. Во время построения данные хранятся с использованием MSBuild примитивы, включая [Элемент Item \(MSBuild\)](../../msbuild/item-element-msbuild.md) и [Элемент Property \(MSBuild\)](../../msbuild/property-element-msbuild.md). Данные времени разработки, то есть данные, относящиеся к типу проекта и любых подтипов связанный проект, хранится в свободной форме XML, зарезервированного для ее.  
  
 MSBuild не имеет встроенную поддержку для настройки объектов, но условные атрибуты для указания данных, относящихся к конфигурации. Например:  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Дополнительные сведения о условные атрибуты в разделе [Условные конструкции](../../msbuild/msbuild-conditional-constructs.md).  
  
### Расширение для данного типа проекта MSBuild  
 Интерфейсы MSBuild и API\-интерфейсы могут быть изменены в будущих версиях [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Таким образом рекомендуется использовать классы framework \(MPF\) управляемых пакетов, так как они обеспечивают защиту от изменений.  
  
 Платформа управляемых пакетов для проектов \(MPFProj\) предоставляет вспомогательные классы для создания и управления новой системы проектов. Найти источник кода и компиляция инструкции в [MPF проектов — Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Ниже приведены классы MPF конкретного проекта.  
  
|Класс|Реализация|  
|-----------|----------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` класс является оболочкой для элементов MSBuild.  
  
#### Vs генераторов одного файла. Задачи MSBuild  
 Один файл генераторы доступ\-только во время разработки, но задачи MSBuild, которые могут использоваться во время разработки и во время построения. Для обеспечения максимальной гибкости таким образом, используйте задачи MSBuild для преобразования и создания кода. Для получения дополнительной информации см. [Пользовательские инструменты](../../extensibility/internals/custom-tools.md).  
  
## См. также  
 [Справочные сведения о MSBuild](../../msbuild/msbuild-reference.md)   
 [MSBuild](http://msdn.microsoft.com/ru-ru/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [Пользовательские инструменты](../../extensibility/internals/custom-tools.md)