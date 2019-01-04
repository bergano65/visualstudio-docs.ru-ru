---
title: Регистрация и Отмена регистрации пакетов VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 21745b0e8a17d580e916f33246093e763811b69a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961024"
---
# <a name="register-and-unregister-vspackages"></a>Регистрация и Отмена регистрации пакетов VSPackage
Атрибуты можно использовать для регистрации VSPackage, но  
  
## <a name="register-a-vspackage"></a>Регистрация VSPackage  
 Атрибуты можно использовать для управления регистрацией управляемых пакетов VSPackage. Все сведения о регистрации, содержащийся в *.pkgdef* файл. Дополнительные сведения о регистрации на основе файлов, см. в разделе [служебная программа CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).  
  
 Приведенный ниже показано, как использовать атрибуты стандартной регистрации для регистрации VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{
    // ...
}  
```  
  
## <a name="unregister-an-extension"></a>Отмена регистрации расширения  
 Если вы экспериментировали с большим количеством разных пакетов VSPackage и удалить их из экспериментальный экземпляр, можно просто запустить **Сброс** команды. Найдите **Сброс экспериментального экземпляра Visual Studio** на начальной странице компьютера, или выполните следующую команду из командной строки:  
  
```cmd  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Если вы хотите удалить расширение, которое вы установили на свой экземпляр разработки Visual Studio, перейдите на страницу **средства** > **расширения и обновления**, найдите нужное расширение и нажмите кнопку  **Удалить**.  
  
 Если для какой-либо причине ни один из этих методов выполняется успешно при удалении расширения, сборки VSPackage из командной строки можно отменить регистрацию следующим образом:  
  
```cmd  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Использование пользовательского атрибута регистрации для регистрации расширения  
  
В некоторых случаях может потребоваться создать новый атрибут регистрации для модуля. Чтобы добавить новый раздел реестра или добавить новые значения для существующих ключей можно использовать атрибуты регистрации. Новый атрибут должен быть производным от <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, и его необходимо переопределить <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> и <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> методы.  
  
### <a name="create-a-custom-attribute"></a>Создание пользовательского атрибута  
  
Ниже показано, как создать новый атрибут регистрации.  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
public class CustomRegistrationAttribute : RegistrationAttribute  
{  
}  
```  
  
 <xref:System.AttributeUsageAttribute> Используется в классах атрибутов для указания элемент программы (класс, метод и т.д.) который этот атрибут относится ли он может использоваться более одного раза и ли он может быть унаследован.  
  
### <a name="create-a-registry-key"></a>Создание раздела реестра  
  
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
  
### <a name="create-a-new-value-under-an-existing-registry-key"></a>Создайте новое значение существующего раздела реестра  
  
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
