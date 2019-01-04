---
title: Как расширение перехода
ms.date: 06/25/2017
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: gregvanl
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 809ca83d164b4cb589f19438b1fc5672cc1b4b8e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880956"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Как выполнить Обеспечить совместимость с Visual Studio 2017 и Visual Studio 2015 расширения

В этом документе объясняется, как сделать приема-передачи между Visual Studio 2015 и Visual Studio 2017 проекты расширения среды. После завершения обновления, проекта будут иметь возможность открыть, построения, установить и запустить в Visual Studio 2015 и Visual Studio 2017. Как ссылка, некоторые расширения, которые могут приема-передачи между Visual Studio 2015 и Visual Studio 2017 можно найти в [примеры расширяемости VS SDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Если требуется только создать в Visual Studio 2017, но выходные данные VSIX для выполнения в Visual Studio 2015 и Visual Studio 2017, затем ссылаться на [документа миграции расширение](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

> [!NOTE]
> Из-за изменения между версиями Visual Studio некоторые вещи, которые работали в одной версии не работают в другой. Убедитесь, что вы пытаетесь получить доступ к функции, доступны в обеих версиях расширения будет непредвиденные результаты.

Ниже приводится объяснение действий, которые вы выполните в этом документе, выполнение цикла обработки VSIX:

1. Импортируйте правильные пакеты NuGet.
2. Обновите манифест расширения:
    * Целевой объект установки
    * Предварительные требования
3. Обновите CSProj:
    * Обновление `<MinimumVisualStudioVersion>`.
    * Добавление `<VsixType>` свойство.
    * Добавить свойство отладки `($DevEnvDir)` 3 раза.
    * Добавление условий для импорта средства сборки и целевых объектов.

4. Сборка и тестирование

## <a name="environment-setup"></a>Настройка среды

В этом документе предполагается, что на вашем компьютере установлены следующие компоненты:

* Visual Studio 2015 с установлен пакет SDK для VS
* Visual Studio 2017 с установленной рабочей нагрузкой расширяемости

## <a name="recommended-approach"></a>Рекомендуемый подход

Настоятельно рекомендуется начать обновление с Visual Studio 2015, а не Visual Studio 2017. Основное преимущество разработки в Visual Studio 2015 — убедитесь, что вы не ссылаются на сборки, которые недоступны в Visual Studio 2015. В этом случае разработки в Visual Studio 2017, есть риск, что может привести к зависимость от сборки, которая существует только в Visual Studio 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Убедитесь, что нет ссылки в файле project.json

Далее в этом документе мы вставим операторы условного импорта в для вашей **.csproj* файл.  Это не будет работать, если ссылки NuGet хранятся в *project.json*. Таким образом, рекомендуется переместить все ссылки NuGet на *packages.config* файла.
Если проект содержит *project.json* файла:

* Запишите все ссылки в *project.json*.
* Из **обозревателе решений**, удалить *project.json* файл из проекта. При этом будут удалены *project.json* файла и удаляет его из проекта.
* Добавьте ссылки на пакеты NuGet обратно в проект:
    * Щелкните правой кнопкой мыши **решение** и выберите **управление пакетами NuGet для решения**.
    * Visual Studio автоматически создает *packages.config* файл для вас.

> [!NOTE]
> Если проект содержал EnvDTE пакеты, их нужно добавить, щелкнув правой кнопкой мыши **ссылки** выбора **добавьте ссылку на** и добавив соответствующую ссылку.  Использование пакетов NuGet может вызывать ошибки при попытке сборки проекта.

## <a name="add-appropriate-build-tools"></a>Добавление средств соответствующие построения

Необходимо чтобы добавить средства сборки, которые позволят нам для сборки и отладки соответствующим образом. Корпорация Майкрософт создала сборки для этой вызываемой Microsoft.VisualStudio.Sdk.BuildTasks.

Для создания и развертывания VSIXv3 в Visual Studio 2015 и 2017, потребуются следующие пакеты NuGet:

Версия | Один из таких инструментов
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

Для этого сделайте следующее:

* Добавьте пакет NuGet Microsoft.VisualStudio.Sdk.BuildTasks.14.0 в проект.
* Если проект не содержит Microsoft.VSSDK.BuildTools, добавьте его.
* Убедитесь, версия Microsoft.VSSDK.BuildTools 15.x или более поздней версии.

## <a name="update-extension-manifest"></a>Обновить манифест расширения

### <a name="1-installation-targets"></a>1. Целевые объекты установки

Мы должны сообщить Visual Studio, какие версии для создания VSIX.  Как правило эти ссылки являются либо до версии 14.0 (Visual Studio 2015) или версии 15.0 (Visual Studio 2017).  В нашем случае мы хотим построить VSIX, который установит расширение в обоих случаях, поэтому нам нужно предназначенных для обеих версий.  Если требуется выполнить сборку и установку на версии более ранней, чем 14.0 VSIX, это можно сделать, задав номер более ранней версии; Тем не менее версия 10.0 и более ранних версий больше не поддерживаются.

* Откройте *source.extension.vsixmanifest* файл в Visual Studio.
* Откройте **цели установки** вкладки.
* Изменение **диапазон версий** для [14.0, 16.0).  "[" Указывает Visual Studio 14.0 и все версии за ними.  ")" Указывает Visual Studio для включения всех версий 15.0 до, но не включая версии 16.0.
* Сохраните все изменения и закройте все экземпляры Visual Studio.

![Изображение целевые объекты установки](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Добавление необходимых сборок для *extension.vsixmanifest* файла

Необходимые компоненты — это новая функция в Visual Studio 2017.  Таким образом мы должны основной редактор Visual Studio в качестве необходимого компонента. Так как в конструкторе Visual Studio 2015 VSIX не обрабатывает новый `Prerequisites` разделе, вам потребуется изменить это часть вручную в коде XML.  Кроме того можно открыть Visual Studio 2017 и используйте обновленный конструктор манифеста для вставки предварительные требования.

Чтобы сделать это вручную:

* Перейдите в каталог проекта в проводнике.
* Откройте *extension.vsixmanifest* файл в текстовом редакторе.
* Добавьте следующий тег:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Сохраните и закройте файл.

> [!NOTE]
> Если вы решили сделать это с помощью конструктора VSIX в Visual Studio 2017, необходимо будет вручную изменить версия необходимого компонента, чтобы убедиться, что он совместим со всеми версиями Visual Studio 2017.  Это обусловлено конструктора будет вставлять минимальной версии в качестве текущей версией Visual Studio (например, 15.0.26208.0).  Тем не менее, так как другие пользователи могут иметь более ранней версии, необходимо вручную изменить на 15.0.

На этом этапе файл манифеста выглядит примерно следующим образом:

![Пример необходимых компонентов](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Изменение файла проекта (myproject.csproj)

Рекомендуется иметь ссылку на измененный .csproj, открытые во время выполнения этого шага.  Несколько примеров можно найти [здесь](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  Выберите любой пример расширяемости, найдите *.csproj* для ссылки на файл и выполните следующие действия:

* Перейдите в каталог проекта в **проводнике**.
* Откройте *myproject.csproj* файл в текстовом редакторе.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Обновление MinimumVisualStudioVersion

* Значение минимального visual studio версии `$(VisualStudioVersion)` и добавьте условный оператор, для него.  Добавьте эти теги, если они не существуют.  Убедитесь, что были установлены теги, как показано ниже:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Добавьте свойство VsixType.

* Добавьте следующий тег `<VsixType>v3</VsixType>` группу свойств.

> [!NOTE]
> Рекомендуется, чтобы добавить это ниже `<OutputType></OutputType>` тега.

### <a name="3-add-the-debugging-properties"></a>3. Добавление свойства отладки

* Добавьте следующие группы свойств:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Удалите все экземпляры в следующем примере кода из *.csproj* файла и любые *. csproj.user* файлы:

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Добавление условий для операции импорта средства построения

* Добавить дополнительные условные операторы, чтобы `<import>` теги, которые имеют Microsoft.VSSDK.BuildTools ссылку.  Вставить `'$(VisualStudioVersion)' != '14.0' And` в начале оператора условия.  Эти инструкции будут отображаться в верхнем и нижнем колонтитуле CSPROJ-файле.

Пример:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Добавить дополнительные условные операторы, чтобы `<import>` теги, которые имеют Microsoft.VisualStudio.Sdk.BuildTasks.14.0. Вставить `'$(VisualStudioVersion)' == '14.0' And` в начале оператора условия. Эти инструкции будут отображаться в верхнем и нижнем колонтитуле CSPROJ-файле.

Пример:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Добавить дополнительные условные операторы, чтобы `<Error>` теги, которые имеют Microsoft.VSSDK.BuildTools ссылку.  Это можно сделать путем вставки `'$(VisualStudioVersion)' != '14.0' And` в начале оператора условия. Эти инструкции будут отображаться в нижнем колонтитуле CSPROJ-файле.

Пример:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Добавить дополнительные условные операторы, чтобы `<Error>` теги, которые имеют Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  Вставить `'$(VisualStudioVersion)' == '14.0' And` в начале оператора условия. Эти инструкции будут отображаться в нижнем колонтитуле CSPROJ-файле.

Пример:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Сохраните файл csproj и закройте его.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Проверка устанавливает расширение в Visual Studio 2015 и Visual Studio 2017

На этом этапе проекта должны быть готовы создавать VSIXv3, который можно установить на Visual Studio 2015 и Visual Studio 2017.

* Откройте проект в Visual Studio 2015.
* Построение проекта и убедитесь в правильности сборки VSIX выходных данных.
* Перейдите в каталог проекта.
* Откройте *\bin\Debug* папки.
* Дважды щелкните VSIX-файл и установить расширение на Visual Studio 2015 и Visual Studio 2017.
* Убедитесь, что можно увидеть расширение в **средства** > **расширения и обновления** в **установленные** раздел.
* Попытка выполнения или использовать расширение, чтобы проверить, что он работает.

![Найдите файл VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> Если проект перестает отвечать на запросы с сообщением **при открытии файла**, принудительное завершение работы Visual Studio, перейдите в каталог проекта, Показать скрытые папки и удалите *.vs* папки.