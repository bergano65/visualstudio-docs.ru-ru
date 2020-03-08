---
title: Регистрация и Отмена регистрации пакетов VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 701700ba9d5c6db1e5858a2419e1b2c0fa950ae5
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409142"
---
# <a name="register-and-unregister-vspackages"></a>Регистрация и Отмена регистрации пакетов VSPackage
Для регистрации VSPackage используются атрибуты, но

## <a name="register-a-vspackage"></a>Регистрация пакета VSPackage
 Для управления регистрацией управляемых пакетов VSPackage можно использовать атрибуты. Все сведения о регистрации содержатся в файле *pkgdef* . Дополнительные сведения о регистрации на основе файлов см. в разделе [служебная программа CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).

 В следующем коде показано, как использовать стандартные атрибуты регистрации для регистрации пакета VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Отмена регистрации расширения
 Если вы выполнили эксперимент с множеством различных пакетов VSPackage и хотите удалить их из экспериментального экземпляра, можно просто выполнить команду **Reset** . Найдите **Сброс экспериментального экземпляра Visual Studio** на начальной странице компьютера или выполните следующую команду в командной строке:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Если вы хотите удалить расширение, установленное на экземпляре Visual Studio Development, перейдите в **меню сервис** > **расширения и обновления**, найдите расширение и нажмите кнопку **Удалить**.

 Если по какой бы то ни было из этих методов не удается удалить расширение, можно отменить регистрацию сборки VSPackage в командной строке следующим образом:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Использование пользовательского атрибута регистрации для регистрации расширения

В некоторых случаях может потребоваться создать новый атрибут регистрации для вашего расширения. Атрибуты регистрации можно использовать для добавления новых разделов реестра или для добавления новых значений к существующим ключам. Новый атрибут должен быть производным от <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>и должен переопределять методы <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> и <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>.

### <a name="create-a-custom-attribute"></a>Создание настраиваемого атрибута

В следующем коде показано, как создать новый атрибут регистрации.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 <xref:System.AttributeUsageAttribute> используется в классах атрибутов для указания программного элемента (класса, метода и т. д.), к которому относится атрибут, независимо от того, может ли он использоваться несколько раз и может ли он быть унаследован.

### <a name="create-a-registry-key"></a>Создание раздела реестра

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Создание нового значения в существующем разделе реестра

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

## <a name="see-also"></a>См. также раздел
- [Пакеты VSPackage](../extensibility/internals/vspackages.md)
