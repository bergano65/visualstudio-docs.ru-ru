---
title: Использование пользовательского атрибута регистрации для регистрации расширения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: jillfra
ms.openlocfilehash: a619c5d418df3b9b85ab09cf9b907617ebd81b67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62935788"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>Использование пользовательского атрибута регистрации для регистрации расширения
В некоторых случаях может потребоваться создать новый атрибут регистрации для вашего расширения. Атрибуты регистрации можно использовать для добавления новых разделов реестра или для добавления новых значений к существующим ключам. Новый атрибут должен быть производным от и <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> должен переопределять <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> методы и.  
  
## <a name="creating-a-custom-attribute"></a>Создание настраиваемого атрибута  
 В следующем коде показано, как создать новый атрибут регистрации.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 <xref:System.AttributeUsageAttribute>Класс используется в классах атрибутов для указания программного элемента (класса, метода и т. д.), к которому относится атрибут, независимо от того, может ли он использоваться несколько раз и может ли он быть унаследован.  
  
### <a name="creating-a-registry-key"></a>Создание раздела реестра  
 В следующем коде пользовательский атрибут создает **Пользовательский** подраздел в ключе для регистрируемого пакета VSPackage.  
  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Создание нового значения в существующем разделе реестра  
 Можно добавить пользовательские значения в существующий ключ. В следующем коде показано, как добавить новое значение в ключ регистрации VSPackage.  
  
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