---
title: Использование MSBuild | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f961249ff584f7767dc2505bb20b1fb0961b7dd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704289"
---
# <a name="using-msbuild"></a>Использование MSBuild
MSBuild предоставляет четко определенный, расширяемый формат XML для создания файлов проектов, которые полностью описывают элементы проекта, которые будут построены, строить задачи и создавать конфигурации.

## <a name="general-msbuild-considerations"></a>Общие соображения MSBuild
 Файлы проекта MSBuild, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] например, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] файлы .csproj и .vbproj, содержат данные, которые используются во время сборки, но также могут содержать данные, которые используются во время проектирования. Данные времени сборки хранятся с помощью примитивов MSBuild, включая [элемент элемента (MSBuild)](../../msbuild/item-element-msbuild.md) и [элемент свойства (MSBuild).](../../msbuild/property-element-msbuild.md) Данные по времени проектирования, которые являются данными, относящимися к типу проекта и любым связанным с ним подтипам проекта, хранятся в свободной форме XML, зарезервированной для него.

 MSBuild не имеет нативной поддержки объектов конфигурации, но предоставляет условные атрибуты для указания данных, концентрирующих конкретные конфигурации. Пример:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Для получения дополнительной информации об условных атрибутах [см.](../../msbuild/msbuild-conditional-constructs.md)

### <a name="extending-msbuild-for-your-project-type"></a>Расширение MSBuild для вашего типа проекта
 Интерфейсы MSBuild и AA могут быть [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]изменены в будущих версиях . Поэтому целесообразно использовать классы инфраструктуры управляемых пакетов (MPF), поскольку они обеспечивают защиту от изменений.

 Рамочная программа управляемого пакета для проектов (MPFProj) обеспечивает классы помощников для создания и управления новой системой проектов. Вы можете найти исходный код и инструкции по компиляции на [MPF для проектов - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Конкретные классы MPF для проектов следующие:

|Class|Реализация|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement`класс — это обертка для элементов MSBuild.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Генераторы одного файла против задач MSBuild
 Единые генераторы файлов доступны только в срок проектирования, но задачи MSBuild могут быть использованы в проектно-разбивочное время и время сборки. Таким образом, для максимальной гибкости используйте задачи MSBuild для преобразования и генерации кода. Для получения дополнительной информации [см.](../../extensibility/internals/custom-tools.md)

## <a name="see-also"></a>См. также
- [Ссылка на MSBuild](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Настраиваемые средства](../../extensibility/internals/custom-tools.md)
