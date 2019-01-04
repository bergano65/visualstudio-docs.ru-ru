---
title: Загрузка пакетов VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 477ac9b0b97a7544402f0f70204b8ecf7b43ba95
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53925840"
---
# <a name="load-vspackages"></a>Загрузка пакетов VSPackage
Пакеты VSPackage загружаются в Visual Studio только в том случае, если необходима их функциональность. Например пакет VSPackage загружается при Visual Studio использует фабрику проекта или служба, которая реализует VSPackage. Эта возможность называется отложенной загрузки, которая используется по возможности для повышения производительности.  
  
> [!NOTE]
>  Visual Studio можно определить определенные сведения о пакете VSPackage, например команд, которые предлагает VSPackage, без загрузки VSPackage.  
  
 Пакеты VSPackage может быть присвоено автозагрузки в контексте определенного пользователя пользовательского интерфейса, например, при открытом решении. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Атрибут задает этот контекст.  
  
### <a name="autoload-a-vspackage-in-a-specific-context"></a>Автозагрузка VSPackage в определенном контексте  
  
-   Добавление `ProvideAutoLoad` атрибута к VSPackage атрибуты:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     См. в разделе перечисления полей <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> список контекстов пользовательского интерфейса и их значения GUID.  
  
-   Установите точку останова в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод.  
  
-   Создание пакета VSPackage и начните отладку.  
  
-   Загрузите решение или создайте его.  
  
     Пакет VSPackage, загружает и останавливается в точке останова.  
  
## <a name="force-a-vspackage-to-load"></a>Принудительная загрузка VSPackage  
 В некоторых случаях пакет VSPackage может потребоваться принудительно другом пакете VSPackage для загрузки. Например упрощенный VSPackage может загрузить VSPackage большего размера в контексте, который будет доступен как CMDUIContext.  
  
 Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> способ принудительного VSPackage для загрузки.  
  
-   Вставьте этот код в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> методе VSPackage, которое заставляет другом пакете VSPackage для загрузки:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     При инициализации VSPackage, этот параметр вызывает принудительную `PackageToBeLoaded` для загрузки.  
  
     Загрузка Force для обмена данными VSPackage не следует. Используйте [использования и предоставления служб](../extensibility/using-and-providing-services.md) вместо этого.
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)
