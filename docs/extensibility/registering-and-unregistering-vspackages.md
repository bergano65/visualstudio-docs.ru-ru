---
title: "Регистрация и Отмена регистрации пакетов VSPackage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4443195babbe3f8926633a992aa942dcb80dc3f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="registering-and-unregistering-vspackages"></a>Регистрация и Отмена регистрации пакетов VSPackage
Используйте атрибуты для регистрации VSPackage, но  
  
## <a name="registering-a-vspackage"></a>Регистрация VSPackage  
 Атрибуты можно использовать для управления регистрацией управляемых пакетов VSPackage. Все сведения о регистрации содержится в pkgdef-файл. Дополнительные сведения о регистрации файла см. в разделе [CreatePkgDef программы](../extensibility/internals/createpkgdef-utility.md).  
  
 Следующий код показано, как использовать атрибуты стандартной регистрации для регистрации VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Отмена регистрации расширения  
 Если экспериментировать с большим количеством различных пакетов VSPackage и удалить их из экспериментальный экземпляр, можно просто запустить **Сброс** команды. Найдите **Сброс экспериментального экземпляра Visual Studio** на начальной странице компьютера, или выполните следующую команду из командной строки:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Если вы хотите удалить расширение, установленного на вашем экземпляре разработки Visual Studio, перейдите к **средства / расширения и обновления**, найдите нужное расширение и нажмите кнопку **удаления**.  
  
 Если для какой-либо причине ни один из этих методов выполняется успешно при удалении расширения, сборки VSPackage из командной строки можно отменить регистрацию следующим образом:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Использование пользовательского атрибута регистрации для регистрации расширения  
  
В некоторых случаях может потребоваться создание нового атрибута регистрации для модуля. Чтобы добавить новые разделы реестра или добавить новые значения для существующих ключей можно использовать атрибуты регистрации. Новый атрибут должен быть производным от <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, и его необходимо переопределить <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> и <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> методы.  
  
### <a name="creating-a-custom-attribute"></a>Создание настраиваемого атрибута  
  
Ниже показано, как создать новый атрибут регистрации.  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
```  
  
 <xref:System.AttributeUsageAttribute> Используется в классах атрибутов для указания программного элемента (классов, методов и т. д.) которого этот атрибут относится ли он может использоваться более одного раза и является ли он наследуется.  
  
### <a name="creating-a-registry-key"></a>Создание раздела реестра  
  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Создание нового значения существующего раздела реестра  
  
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