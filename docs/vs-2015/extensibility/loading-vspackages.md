---
title: Загрузка пакетов VSPackage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 805b86802e64c91e52d869b067fac871603019e3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979327"
---
# <a name="loading-vspackages"></a>Загрузка пакетов VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакеты VSPackage загружаются в Visual Studio только в том случае, если необходима их функциональность. Например пакет VSPackage загружается при Visual Studio использует фабрику проекта или служба, которая реализует VSPackage. Эта возможность называется отложенной загрузки, которая используется по возможности для повышения производительности.  
  
> [!NOTE]
>  Visual Studio можно определить определенные сведения о пакете VSPackage, например команд, которые предлагает VSPackage, без загрузки VSPackage.  
  
 Пакеты VSPackage может быть присвоено автозагрузки в контексте определенного пользователя пользовательского интерфейса, например, при открытом решении. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Атрибут задает этот контекст.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Автозагрузка VSPackage в определенном контексте  
  
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
  
## <a name="forcing-a-vspackage-to-load"></a>Принудительная загрузка VSPackage  
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
  
     Загрузка Force для обмена данными VSPackage не следует. Используйте [использование и предоставление службы](../extensibility/using-and-providing-services.md) вместо этого.  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Использование настраиваемого атрибута для регистрации VSPackage  
 В некоторых случаях может потребоваться создать новый атрибут регистрации для модуля. Чтобы добавить новый раздел реестра или добавить новые значения для существующих ключей можно использовать атрибуты регистрации. Новый атрибут должен быть производным от <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, и его необходимо переопределить <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> и <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> методы.  
  
## <a name="creating-a-registry-key"></a>Создание раздела реестра  
 В следующем коде создается пользовательский атрибут **пользовательских** подраздела в разделе для регистрации VSPackage.  
  
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
 Можно добавить пользовательские значения для существующего ключа. Ниже показано, как добавить новое значение для ключа регистрации VSPackage.  
  
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
