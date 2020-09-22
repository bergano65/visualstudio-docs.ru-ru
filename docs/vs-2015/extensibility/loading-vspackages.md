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
ms.openlocfilehash: e20caff476e116ad59430692719bdbbe22c4914c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842704"
---
# <a name="loading-vspackages"></a>Загрузка пакетов VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакеты VSPackage загружаются в Visual Studio только в том случае, если их функциональные возможности необходимы. Например, пакет VSPackage загружается, когда Visual Studio использует фабрику проекта или службу, реализуемую VSPackage. Эта функция называется отложенной загрузкой, которая используется, когда это возможно, для повышения производительности.  
  
> [!NOTE]
> Visual Studio может определить определенные сведения VSPackage, например команды, предлагаемые пакетом VSPackage, без загрузки VSPackage.  
  
 Пакеты VSPackage можно установить в автозагрузки в определенном контексте пользовательского интерфейса, например, когда решение открыто. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>Атрибут задает этот контекст.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Автозагрузка VSPackage в определенном контексте  
  
- Добавьте `ProvideAutoLoad` атрибут к атрибутам VSPackage:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>Список контекстов пользовательского интерфейса и их значений GUID см. в списке полей перечисления.  
  
- Установите точку останова в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> методе.  
  
- Создайте пакет VSPackage и начните отладку.  
  
- Загрузите решение или создайте его.  
  
     Пакет VSPackage загружается и останавливается в точке останова.  
  
## <a name="forcing-a-vspackage-to-load"></a>Принудительная Загрузка VSPackage  
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
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Использование настраиваемого атрибута для регистрации VSPackage  
 В некоторых случаях может потребоваться создать новый атрибут регистрации для вашего расширения. Атрибуты регистрации можно использовать для добавления новых разделов реестра или для добавления новых значений к существующим ключам. Новый атрибут должен быть производным от и <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> должен переопределять <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> методы и.  
  
## <a name="creating-a-registry-key"></a>Создание раздела реестра  
 В следующем коде пользовательский атрибут создает **Пользовательский** подраздел в ключе для регистрируемого пакета VSPackage.  
  
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
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Создание нового значения в существующем разделе реестра  
 Можно добавить пользовательские значения в существующий ключ. В следующем коде показано, как добавить новое значение в ключ регистрации VSPackage.  
  
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
  
## <a name="see-also"></a>См. также:  
 [VSPackages](../extensibility/internals/vspackages.md)
