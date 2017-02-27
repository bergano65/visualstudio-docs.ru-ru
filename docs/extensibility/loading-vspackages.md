---
title: "Загрузка пакетов VSPackages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Пакеты VSPackage Автозагрузка"
  - "пакеты VSPackage, загрузка"
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Загрузка пакетов VSPackages
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Пакеты VSPackage загружаются в Visual Studio только в том случае, если требуется их функциональность. Например VSPackage загружается, когда Visual Studio использует фабрики проекта или служба, которая реализует VSPackage. Эта возможность называется отложенной загрузки, которая используется при любой возможности для повышения производительности.  
  
> [!NOTE]
>  Visual Studio можно определять некоторые сведения VSPackage, такие как команды, доступные в VSPackage, без загрузки VSPackage.  
  
 Пакеты VSPackage может быть присвоено автозагрузки в контексте определенного пользователя пользовательского интерфейса, например, при открытом решении.<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Атрибут задает этот контекст.  
  
### Автозагрузка VSPackage в определенном контексте  
  
-   Добавление `ProvideAutoLoad` атрибут VSPackage атрибуты:  
  
    ```c#  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Перечислимый поля в разделе <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> список контексты пользовательского интерфейса и их значения GUID.  
  
-   Установите точку останова в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод.  
  
-   Построение VSPackage и начать отладку.  
  
-   Загрузите решение или создайте новый.  
  
     VSPackage загружает и останавливается в точке останова.  
  
## Принудительная загрузка VSPackage  
 В некоторых случаях VSPackage может потребоваться принудительно другой VSPackage для загрузки. Например упрощенный VSPackage может загрузить больше VSPackage в контексте, который не доступен как CMDUIContext.  
  
 Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> метод, чтобы принудительно VSPackage для загрузки.  
  
-   Вставьте этот код в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод VSPackage, который вызывает другой VSPackage для загрузки:  
  
    ```c#  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     При инициализации VSPackage вынудит `PackageToBeLoaded` для загрузки.  
  
     Загрузка FORCE следует использовать не обмена VSPackage. Взамен рекомендуется использовать [Использование и предоставления услуг](../extensibility/using-and-providing-services.md).  
  
## Использование настраиваемого атрибута для регистрации VSPackage  
 В некоторых случаях может потребоваться создание нового атрибута регистрации расширения. Атрибуты регистрации можно использовать для добавления новых разделов реестра или добавить новые значения для существующих разделов. Новый атрибут должен быть производным от <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, и его необходимо переопределить <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> и <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> методы.  
  
## Создание раздела реестра  
 В следующем коде создается пользовательский атрибут **пользовательские** подраздела в разделе для VSPackage, который регистрируется.  
  
```c#  
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
  
## Создание нового значения существующего раздела реестра  
 Можно добавить пользовательские значения для существующего ключа. Ниже показано, как добавить новое значение для ключа регистрации VSPackage.  
  
```c#  
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
  
## См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)