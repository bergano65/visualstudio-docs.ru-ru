---
title: Параметры шаблонов проектов и элементов в Visual Studio
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4c76eaf68f63b4f3b8a5713d0b206b395ee7c9f1
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178638"
---
# <a name="template-parameters"></a>Параметры шаблона

Вы можете заменить значения в шаблоне при создании его экземпляра. Чтобы настроить эту функцию, используйте *параметры шаблона*. Они позволяют заменить такие значения, как имена классов и пространства имен в шаблоне. Эти параметры заменяет мастер шаблонов, запускающийся в фоновом режиме, когда пользователь добавляет новый элемент или проект.

## <a name="declaring-and-enabling-template-parameters"></a>Объявление и включение параметров шаблона

Параметры шаблона объявляются в формате $*параметр*$. Пример:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="to-enable-parameter-substitution-in-templates"></a>Включение подстановки параметров в шаблонах

1. В *VSTEMPLATE*-файле шаблона найдите элемент `ProjectItem`, соответствующий элементу, для которого требуется включить замену параметров.

1. Задайте атрибуту `ReplaceParameters` элемента `ProjectItem` значение `true`.

1. В файле кода для элемента проекта укажите соответствующие параметры. Например, следующий параметр указывает, что безопасное имя проекта используется для пространства имен в файле:

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

## <a name="example-use-the-project-name-for-a-file-name"></a>Пример: использование имени проекта в качестве имени файла

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

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Пример: использование безопасного имени проекта в качестве имени пространства имен

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

В *VSTEMPLATE*-файл для шаблона проекта включите атрибут `ReplaceParameters="true"` при ссылке на файл:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>См. также

- [Настройка шаблонов](../ide/customizing-project-and-item-templates.md)
- [Практическое руководство. Создание шаблонов проектов](../ide/how-to-create-project-templates.md)
- [Справочник по схемам шаблонов](../extensibility/visual-studio-template-schema-reference.md)
