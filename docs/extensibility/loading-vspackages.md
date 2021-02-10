---
title: Загрузка пакетов VSPackage | Документация Майкрософт
description: Сведения о загрузке пакетов VSPackage в Visual Studio, включая отложенную загрузку, которая используется, когда это возможно, для повышения производительности.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f87b5bcc94ed11e18de763bd1db7c59bdc4796fc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966387"
---
# <a name="load-vspackages"></a>Загрузка пакетов VSPackage
Пакеты VSPackage загружаются в Visual Studio только в том случае, если их функциональные возможности необходимы. Например, пакет VSPackage загружается, когда Visual Studio использует фабрику проекта или службу, реализуемую VSPackage. Эта функция называется отложенной загрузкой, которая используется, когда это возможно, для повышения производительности.

> [!NOTE]
> Visual Studio может определить определенные сведения VSPackage, например команды, предлагаемые пакетом VSPackage, без загрузки VSPackage.

 Пакеты VSPackage можно установить в автозагрузки в определенном контексте пользовательского интерфейса, например, когда решение открыто. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>Атрибут задает этот контекст.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Автозагрузки VSPackage в определенном контексте

- Добавьте `ProvideAutoLoad` атрибут к атрибутам VSPackage:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>Список контекстов пользовательского интерфейса и их значений GUID см. в списке полей перечисления.

- Установите точку останова в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> методе.

- Создайте пакет VSPackage и начните отладку.

- Загрузите решение или создайте его.

     Пакет VSPackage загружается и останавливается в точке останова.

## <a name="force-a-vspackage-to-load"></a>Принудительная Загрузка VSPackage
 В некоторых обстоятельствах пакету VSPackage может потребоваться принудительно загрузить другой пакет VSPackage. Например, упрощенный пакет VSPackage может загрузить более крупный пакет VSPackage в контексте, недоступном в качестве Кмдуиконтекст.

 Для <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> принудительной загрузки VSPackage можно использовать метод.

- Вставьте этот код в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод VSPackage, который вызывает загрузку другого пакета VSPackage:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     После инициализации VSPackage будет принудительно `PackageToBeLoaded` загружен.

     Принудительная загрузка не должна использоваться для связи VSPackage. Используйте вместо этого использование [и предоставление служб](../extensibility/using-and-providing-services.md) .

## <a name="see-also"></a>См. также раздел
- [VSPackages](../extensibility/internals/vspackages.md)
