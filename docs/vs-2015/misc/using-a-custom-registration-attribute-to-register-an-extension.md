---
title: С помощью пользовательского атрибута регистрации для регистрации расширения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: jillfra
ms.openlocfilehash: a619c5d418df3b9b85ab09cf9b907617ebd81b67
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990432"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>Использование пользовательского атрибута регистрации для регистрации расширения
В некоторых случаях может потребоваться создать новый атрибут регистрации для модуля. Чтобы добавить новый раздел реестра или добавить новые значения для существующих ключей можно использовать атрибуты регистрации. Новый атрибут должен быть производным от <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, и его необходимо переопределить <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> и <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> методы.  
  
## <a name="creating-a-custom-attribute"></a>Создание настраиваемого атрибута  
 Ниже показано, как создать новый атрибут регистрации.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 <xref:System.AttributeUsageAttribute> Используется в классах атрибутов для указания элемент программы (класс, метод и т.д.) который этот атрибут относится ли он может использоваться более одного раза и ли он может быть унаследован.  
  
### <a name="creating-a-registry-key"></a>Создание раздела реестра  
 В следующем коде создается пользовательский атрибут **пользовательских** подраздела в разделе для регистрации VSPackage.  
  
```  
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
 Можно добавить пользовательские значения для существующего ключа. Ниже показано, как добавить новое значение для ключа регистрации VSPackage.  
  
```  
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