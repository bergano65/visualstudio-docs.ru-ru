---
title: Параметры шаблонов проектов и элементов в Visual Studio | Документы Майкрософт
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c49514aeb164040ea374371cae6a61d1f7eb8948
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="template-parameters"></a>Параметры шаблона

С помощью параметров в шаблонах вы можете заменить значения в ключевых частях шаблона, например имена классов и пространства имен, при создании экземпляра шаблона. Эти параметры заменяются с помощью мастера шаблонов, запускающегося в фоновом режиме, когда пользователь нажимает кнопку **ОК** или **Добавить** в диалоговом окне **Новый проект** или **Добавление нового элемента**.

## <a name="declaring-and-enabling-template-parameters"></a>Объявление и включение параметров шаблона

Параметры шаблона объявляются в формате $*параметр*$. Пример:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="to-enable-parameter-substitution-in-templates"></a>Включение подстановки параметров в шаблонах

1. В VSTEMPLATE-файле шаблона найдите элемент `ProjectItem`, соответствующий элементу, для которого требуется включить замену параметров.

1. Задайте атрибуту `ReplaceParameters` элемента `ProjectItem` значение `true`.

1. В файле кода для элемента проекта укажите соответствующие параметры. Например, следующий параметр указывает, что безопасное имя проекта следует использовать для пространства имен в файле:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Зарезервированные параметры шаблона

В таблице ниже перечислены параметры зарезервированного шаблона, которые могут использоваться любым шаблоном.

|Параметр|Описание:|
|---------------|-----------------|
|clrversion|Текущая версия среды CLR.|
|guid[1–10]|GUID, используемый для замены GUID проекта в файле проекта. Можно указать до 10 уникальных GUID (например, `guid1`).|
|itemname|Имя, указанное пользователем в диалоговом окне **Добавление нового элемента**.|
|machinename|Имя текущего компьютера (например, Computer01).|
|projectname|Имя, указанное пользователем в диалоговом окне **Новый проект**.|
|registeredorganization|Значение раздела реестра из HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|rootnamespace|Корневое пространство имен для текущего проекта. Этот параметр применяется только к шаблонам элементов.|
|safeitemname|Имя, указанное пользователем в диалоговом окне **Добавление нового элемента**, с удаленными небезопасными символами и пробелами.|
|safeprojectname|Имя, указанное пользователем в диалоговом окне **Новый проект**, с удаленными небезопасными символами и пробелами.|
|время|Текущее время в формате ДД/ММ/ГГГГ 00:00:00.|
|SpecificSolutionName|Имя решения. Если установлен флажок "create solution directory" (Создать каталог решения), `SpecificSolutionName` имеет имя решения. Если флажок "create solution directory" (Создать каталог решения) не установлен, `SpecificSolutionName` пусто.|
|userdomain|Домен текущего пользователя.|
|Имя пользователя|Имя текущего пользователя.|
|webnamespace|Имя текущего веб-сайта. Этот параметр используется в шаблоне веб-формы, чтобы гарантировать уникальные имена классов. Если веб-сайт находится в корневом каталоге веб-сервера, этот параметр шаблона разрешается в корневой каталог веб-сервера.|
|год|Текущий год в формате ГГГГ.|

> [!NOTE]
> Параметры шаблонов зависят от регистра символов.

## <a name="custom-template-parameters"></a>Настраиваемые параметры шаблона

Вы можете указать собственные параметры шаблона и значения в дополнение к зарезервированным параметрам шаблона по умолчанию, которые используются во время замены параметров. Дополнительные сведения см. в разделе [Элемент CustomParameters (шаблоны Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-using-the-project-name-for-a-file-name"></a>Пример: использование имени проекта в качестве имени файла

Можно указать переменные имена файлов для элементов проекта с помощью параметра в атрибуте `TargetFileName`.

В следующем примере указывается, что имя исполняемого файла использует имя проекта, заданное `$projectname$`.

```xml
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-using-the-safe-project-name-for-the-namespace-name"></a>Пример: использование безопасного имени проекта в качестве имени пространства имен

Чтобы использовать безопасное имя проекта для пространства имен в файле класса C#, используйте следующий синтаксис:

```csharp
namespace $safeprojectname$
{
    public class Class1
    {
        public Class1()
        { }
    }
}
```

В VSTEMPLATE-файл для шаблона проекта включите атрибут `ReplaceParameters="true"` при ссылке на файл:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>См. также

[Настройка шаблонов](../ide/customizing-project-and-item-templates.md)  
[Практическое руководство. Создание шаблонов проектов](../ide/how-to-create-project-templates.md)