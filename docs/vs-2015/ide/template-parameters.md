---
title: Параметры шаблона | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ef4e1a6e3c56df744ce5375a1cb3a1dbd53a6fad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238905"
---
# <a name="template-parameters"></a>Параметры шаблона
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью параметров в шаблонах вы можете заменить значения в ключевых частях шаблона, например имена классов и пространства имен, при создании экземпляра шаблона. Эти параметры заменяются с помощью мастера шаблонов, запускающегося в фоновом режиме, когда пользователь нажимает кнопку **ОК** в диалоговом окне **Новый проект** или **Добавление нового элемента**.  
  
## <a name="declaring-and-enabling-template-parameters"></a>Объявление и включение параметров шаблона  
 Параметры шаблона объявляются в формате $*параметр*$. Пример:  
  
-   $safeprojectname$  
  
-   $guid1$  
  
-   $guid5$  
  
#### <a name="to-enable-parameter-substitution-in-templates"></a>Включение подстановки параметров в шаблонах  
  
1.  В VSTEMPLATE-файле шаблона найдите элемент `ProjectItem`, соответствующий элементу, для которого требуется включить замену параметров.  
  
2.  Задайте атрибуту `ReplaceParameters` элемента `ProjectItem` значение `true`.  
  
3.  В файле кода для элемента проекта укажите соответствующие параметры. Например, следующий параметр указывает, что безопасное имя проекта следует использовать для пространства имен в файле:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
## <a name="reserved-template-parameters"></a>Зарезервированные параметры шаблона  
 В таблице ниже перечислены параметры зарезервированного шаблона, которые могут использоваться любым шаблоном.  
  
> [!NOTE]
>  Параметры шаблонов зависят от регистра символов.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`clrversion`|Текущая версия среды CLR.|  
|`GUID [1-10]`|GUID, используемый для замены GUID проекта в файле проекта. Можно указать до 10 уникальных GUID (например, `guid1)`).|  
|`itemname`|Имя, указанное пользователем в диалоговом окне **Добавление нового элемента**.|  
|`machinename`|Имя текущего компьютера (например, Computer01).|  
|`projectname`|Имя, указанное пользователем в диалоговом окне **Новый проект**.|  
|`registeredorganization`|Значение раздела реестра из HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|  
|`rootnamespace`|Корневое пространство имен для текущего проекта. Этот параметр применяется только к шаблонам элементов.|  
|`safeitemname`|Имя, указанное пользователем в диалоговом окне **Добавление нового элемента**, с удаленными небезопасными символами и пробелами.|  
|`safeprojectname`|Имя, указанное пользователем в диалоговом окне **Новый проект**, с удаленными небезопасными символами и пробелами.|  
|`time`|Текущее время в формате ДД/ММ/ГГГГ 00:00:00.|  
|`SpecificSolutionName`|Имя решения. Если установлен флажок "create solution directory" (Создать каталог решения), `SpecificSolutionName` имеет имя решения. Если флажок "create solution directory" (Создать каталог решения) не установлен, `SpecificSolutionName` пусто.|  
|`userdomain`|Домен текущего пользователя.|  
|`username`|Имя текущего пользователя.|  
|`webnamespace`|Имя текущего веб-сайта. Этот параметр используется в шаблоне веб-формы, чтобы гарантировать уникальные имена классов. Если веб-сайт находится в корневом каталоге веб-сервера, этот параметр шаблона разрешается в корневой каталог веб-сервера.|  
|`year`|Текущий год в формате ГГГГ.|  
  
## <a name="custom-template-parameters"></a>Настраиваемые параметры шаблона  
 Вы можете указать собственные параметры шаблона и значения в дополнение к зарезервированным параметрам шаблона по умолчанию, которые используются во время замены параметров. Дополнительные сведения см. в разделе [Элемент CustomParameters (шаблоны Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md).  
  
## <a name="example-replacing-files-names"></a>Пример: замена имен файлов  
 Вы можете указать переменные имена файлов для элементов проекта с помощью параметра с атрибутом `TargetFileName`. Например, можно указать, что файл EXE использует имя проекта, заданное `$projectname$`, в качестве имени файла.  
  
```  
<TemplateContent>  
    <ProjectItem  
        ReplaceParameters="true"  
        TargetFileName="$projectname$.exe">  
            File1.exe  
    </ProjectItem>  
      ...  
</TemplateContent>  
```  
  
## <a name="example-using-the-project-name-for-the-namespace-name"></a>Пример: использование имени проекта в качестве имени пространства имен  
 Чтобы использовать имя проекта для пространства имен в файле класса Visual C# — Class1.cs, используйте следующий синтаксис:  
  
```  
#region Using directives  
  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
#endregion  
  
namespace $safeprojectname$  
{  
    public class Class1  
        {  
            public Class1()  
                {  
  
                }  
         }  
}  
```  
  
 В VSTEMPLATE-файл для шаблона проекта включите следующий XML-код при ссылке на файл Class1.cs:  
  
```  
<TemplateContent>  
    <ProjectItem ReplaceParameters="true">  
        Class1.cs  
    </ProjectItem>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>См. также  
 [Настройка шаблонов](../ide/customizing-project-and-item-templates.md)



