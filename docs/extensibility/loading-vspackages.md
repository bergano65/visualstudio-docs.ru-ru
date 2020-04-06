---
title: Загрузка VSPackages Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c221bf06ef3b7e37e2afc1856f3e54fe5ad95e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702968"
---
# <a name="load-vspackages"></a>Нагрузка VSПакеты
VSPackages загружаются в Visual Studio только тогда, когда требуется их функциональность. Например, VSPackage загружается, когда Visual Studio использует проектную фабрику или службу, которую реализует VSPackage. Эта функция называется задержкой загрузки, которая используется по возможности для повышения производительности.

> [!NOTE]
> Visual Studio может определить определенную информацию VSPackage, например команды, которые предлагает VSPackage, без загрузки VSPackage.

 VSPackages можно настроить для автоматической загрузки в определенном контексте пользовательского интерфейса (UI), например, когда решение открыто. Атрибут <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> задает этот контекст.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Автоматическая загрузка VSPackage в определенном контексте

- Добавьте `ProvideAutoLoad` атрибут атрибуты VSPackage:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Ознакомьтесь с перечисленными полями <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> для списка контекстов интерфейса и их значений GUID.

- Установите точку <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> разрыва в методе.

- Создайте VSPackage и начните отладку.

- Загрузите решение или создайте его.

     VSPackage загружается и останавливается в точке разрыва.

## <a name="force-a-vspackage-to-load"></a>Заставить VSPackage для загрузки
 При некоторых обстоятельствах VSPackage, возможно, придется заставить другой VSPackage быть загружены. Например, легкий VSPackage может загрузить больший VSPackage в контексте, который недоступен в качестве CMDUIContext.

 Вы можете <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> использовать метод, чтобы заставить VSPackage для загрузки.

- Вставьте этот <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> код в метод VSPackage, который заставляет другой VSPackage загружать:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Когда VSPackage инициализирован, `PackageToBeLoaded` он заставит загрузиться.

     Силовая нагрузка не должна использоваться для связи VSPackage. Используйте [и предоставляя услуги](../extensibility/using-and-providing-services.md) вместо этого.

## <a name="see-also"></a>См. также
- [Пакеты VSPackage](../extensibility/internals/vspackages.md)
