---
title: "Загрузка пакетов VSPackage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 94db8d3bb95e254a3fa528a424048162916fce99
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="loading-vspackages"></a>Загрузка пакетов VSPackage
Пакеты VSPackage, загружаются в Visual Studio только в том случае, если требуется их функциональность. Например пакет VSPackage загружается при Visual Studio использует фабрики проектов или служба, которая реализует VSPackage. Эта возможность называется отложенной загрузки, который используется, по возможности для повышения производительности.  
  
> [!NOTE]
>  Visual Studio можно определить определенные сведения о пакете VSPackage, такими как команды, которые предлагает VSPackage, без загрузки VSPackage.  
  
 Пакеты VSPackage может быть присвоено автозагрузки (AutoLoad) в контексте определенного пользователя пользовательского интерфейса, например, когда открыто решение. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Атрибут задает этот контекст.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Автозагрузка VSPackage в определенном контексте  
  
-   Добавить `ProvideAutoLoad` атрибут VSPackage атрибуты:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Перечислимый поля в разделе <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> список контексты пользовательского интерфейса и их значений GUID.  
  
-   Установите точку останова в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод.  
  
-   Построение пакета VSPackage и начните отладку.  
  
-   Загрузите решение или создайте новый.  
  
     Пакет VSPackage, загружает и останавливается в точке останова.  
  
## <a name="forcing-a-vspackage-to-load"></a>Принудительная загрузка VSPackage  
 В некоторых случаях пакет VSPackage может потребоваться принудительно другой VSPackage для загрузки. Например упрощенный VSPackage может загрузить больше VSPackage в контексте, который будет доступен как CMDUIContext.  
  
 Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> способ принудительного VSPackage для загрузки.  
  
-   Вставьте этот код в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод VSPackage, который вызывает другой VSPackage для загрузки:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     При инициализации VSPackage, этот параметр вызывает принудительную `PackageToBeLoaded` для загрузки.  
  
     Загрузка FORCE следует не используется для связи VSPackage. Используйте [использование и служб, предоставляя](../extensibility/using-and-providing-services.md) вместо него.  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>С помощью настраиваемого атрибута зарегистрировать VSPackage  
 В некоторых случаях может потребоваться создание нового атрибута регистрации для модуля. Чтобы добавить новые разделы реестра или добавить новые значения для существующих ключей можно использовать атрибуты регистрации. Новый атрибут должен быть производным от <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, и его необходимо переопределить <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> и <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> методы.  
  
## <a name="creating-a-registry-key"></a>Создание раздела реестра  
 В следующем коде создается пользовательский атрибут **пользовательские** подразделов раздела для регистрации VSPackage.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Создание нового значения существующего раздела реестра  
 Можно добавить пользовательские значения для существующего ключа. Следующий код демонстрирует добавление нового значения с ключом регистрации VSPackage.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)