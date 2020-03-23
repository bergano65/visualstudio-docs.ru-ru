---
title: Регистрация и нерегистрация VSPackages (ru) Документы Майкрософт
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301587"
---
# <a name="register-and-unregister-vspackages"></a>Регистрация и распаковка VSPackages
Вы используете атрибуты для регистрации VSPackage, но

## <a name="register-a-vspackage"></a>Регистрация VSPackage
 Вы можете использовать атрибуты для контроля регистрации управляемых VSPackages. Вся регистрационная информация содержится в файле *.pkgdef.* Для получения дополнительной информации о [CreatePkgDef utility](../extensibility/internals/createpkgdef-utility.md)регистрации файлов см.

 Следующий код показывает, как использовать стандартные атрибуты регистрации для регистрации VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Отмена регистрации расширения
 Если вы экспериментировали с большим количеством различных VSPackages и хотите удалить их из экспериментального экземпляра, вы можете просто запустить команду **сбросить.** Ищите **перезагрузку экспериментальной** версии Visual Studio на стартовой странице компьютера или запускайте эту команду из командной строки:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Если вы хотите удалить расширение, которое вы установили на экземпляре разработки Visual Studio, перейдите на расширения**и обновления инструментов,** **Tools** > найдите расширение и нажмите **Uninstall.**

 Если по какой-либо причине ни один из этих методов не удается установить расширение, вы можете отменить сборку VSPackage от командной строки следующим образом:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Используйте пользовательский атрибут регистрации для регистрации расширения

В некоторых случаях может потребоваться создать новый атрибут регистрации для расширения. Атрибуты регистрации можно использовать для добавления новых ключей реестра или добавления новых значений к существующим ключам. Новый атрибут должен <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>вытекать из, <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> и <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> он должен переопределить и методы.

### <a name="create-a-custom-attribute"></a>Создание настраиваемого атрибута

Следующий код показывает, как создать новый атрибут регистрации.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 Используется <xref:System.AttributeUsageAttribute> на классах атрибутов для указания элемента программы (класса, метода и т.д.), к которому относится атрибут, можно ли его использовать более одного раза и можно ли его унаследовать.

### <a name="create-a-registry-key"></a>Создание ключа реестра

В следующем коде пользовательский атрибут создает **подключку Custom** под ключом для зарегистрированного VSPackage.

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Создание нового значения под существующим ключом реестра

Пользовательские значения можно добавить к существующему ключу. Следующий код показывает, как добавить новое значение к ключу регистрации VSPackage.

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
