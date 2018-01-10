---
title: "Как: двунаправленное расширения для Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 06/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
caps.latest.revision: "1"
author: willbrown
ms.author: willbrown
manager: justinclareburt
ms.workload: willbrown
ms.openlocfilehash: b51673daa7a8c3526ad7de7f7cfdeac6a91d3b4b
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Как: расширения создать совместимый с 2017 г. Visual Studio и Visual Studio 2015

В этом документе объясняется, как сделать проекты расширяемости приема-передачи между Visual Studio 2015 и Visual Studio 2017 г. После завершения обновления, проект будет открывать, построения, установить и запустить в Visual Studio 2015 и Visual Studio 2017 г.  Как ссылка, можно найти некоторые расширения, которые можно приема-передачи между Visual Studio 2015 и Visual Studio 2017 г [здесь](https://github.com/Microsoft/VSSDK-Extensibility-Samples) в примерах расширяемости корпорации Майкрософт.

Если планируется только сборки в Visual Studio 2017 г., но выходные данные VSIX для выполнения в Visual Studio 2015 и Visual Studio 2017 г., затем ссылаться на [документа миграции расширение](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

>**Примечание:** из-за изменений в Visual Studio между версиями некоторые аспекты, которые работали в одной версии не будет другой. Убедитесь, что вы пытаетесь получить доступ к возможности доступны в обеих версиях или будет иметь расширение непредвиденные результаты.

Ниже приведен обзор шагов, которые будут выполнены в этом документе для обратного преобразования VSIX.

1. Импортируйте правильные пакеты NuGet.
2. Обновление манифеста расширения:
    * Целевой объект установки
    * Предварительные требования
3. Обновление CSProj:
    * Обновление `<MinimumVisualStudioVersion>`.
    * Добавить `<VsixType>` свойство.
    * Добавить свойство отладки `($DevEnvDir)` 3 раза.
    * Добавление условий для импорта средствах сборки и целевых объектов.

4. Построение и тестирование

## <a name="environment-setup"></a>Настройка среды

В этом документе предполагается, что на компьютере установлены следующие компоненты:

* Visual Studio 2015 с установленный пакет SDK для VS
* Visual Studio 2017 г. с рабочей нагрузкой расширяемости установлен

## <a name="recommended-approach"></a>Рекомендуемый подход

Настоятельно рекомендуется начать обновление с Visual Studio 2015, а не Visual Studio 2017 г. Основным преимуществом разработки в Visual Studio 2015 — убедитесь, что вы не ссылаются на сборки, которые не доступны в Visual Studio 2015. Разработка решений в Visual Studio 2017 г. в этом случае есть риск, может возникнуть зависимость от сборки, которая существует только в Visual Studio 2017 г.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Убедитесь, что нет ссылки в файл project.json

Далее в этом документе вставим операторы условного импорта в файл *.csproj.  Это не поможет, если ссылки NuGet хранятся в файле project.json. Таким образом рекомендуется переместить все NuGet ссылки на файл packages.config.
Если проект содержит файл project.json:

* Запишите ссылки в файле project.json.
* В обозревателе решений удалите файл project.json из проекта.
    * Будет удалено в файл project.json, а удалить его из проекта.
* Добавление ссылок NuGet обратно в проект.
    * Щелкните правой кнопкой мыши решение и выберите **управление пакетами NuGet для решения...**
    * Visual Studio автоматически создает файл packages.config

>**Примечание:** Если проект содержит EnvDTE пакетов, их нужно добавить, щелкнув правой кнопкой мыши **ссылки** выбора **добавить ссылку** и добавления соответствующие ссылки.  С помощью пакетов NuGet может создавать ошибки при попытке выполнить сборку проекта.

## <a name="adding-appropriate-build-tools"></a>Добавление средств соответствующее построение

Нам необходимо чтобы добавить средства сборки, которые мы будем создавать и отлаживать соответствующим образом. Корпорация Майкрософт создала сборки для этой вызываемой Microsoft.VisualStudio.Sdk.BuildTasks.

Чтобы построить и развернуть VSIXv3 в Visual Studio 2015 и 2017 г., потребуются следующие пакеты NuGet.

Версия | Средства построения
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

Для этого:

* Добавьте пакет NuGet Microsoft.VisualStudio.Sdk.BuildTasks.14.0 в проект.
* Если проект не содержит Microsoft.VSSDK.BuildTools, добавьте его.
* Убедитесь, Microsoft.VSSDK.BuildTools 15.x или выше.

## <a name="update-extension-manifest"></a>Обновление манифеста расширения

### <a name="1-installation-targets"></a>1. Целевые объекты установки

Необходимо указать для построения VSIX какие версии Visual Studio.  Обычно эти ссылки являются либо до версии 14.0 (Visual Studio 2015) или 15.0 (Visual Studio 2017 г.).  В нашем случае мы хотим построить файл VSIX, который установит расширение для обоих, поэтому необходимо использовать обе версии.  Если требуется выполнить сборку и установку в версиях, более ранних, чем 14.0 вашей VSIX, это можно сделать, задав более ранних номер версии; Однако версии 10.0 и более ранних версий больше не поддерживаются.

* Откройте файл source.extension.vsixmanifest в Visual Studio.
* Откройте **цели установки** вкладки.
* Изменение **диапазон версий** для [14.0, 16,0).  "[" Среда Visual Studio входят версии 14.0 и все за ними.  ")" Среда Visual Studio включают в себя все версии 15.0, но не включающую 16.0 версии.
* Сохраняет все изменения и закрыть все экземпляры Visual Studio.

![Изображение для целевых объектов установки](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Добавление необходимых сборок в файл extension.vsixmanifest

Необходимые компоненты — это новая функция, с помощью Visual Studio 2017 г.  В этом случае нужно базового редактора Visual Studio как необходимый компонент. Поскольку конструктор Visual Studio 2015 VSIX не может обрабатывать новый `Prerequisites` раздела, необходимо будет изменить эту часть вручную в XML-коде.  Или можно открыть Visual Studio 2017 г. и использовать обновленный конструктора манифестов для вставки необходимых компонентов.

Чтобы сделать это вручную:

* Перейдите в каталог проекта в проводнике.
* Откройте `extension.vsixmanifest` файл в текстовом редакторе.
* Добавьте следующий тег:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Сохраните и закройте файл.

>**Примечание:** при выборе для этого конструктора VSIX в Visual Studio 2017 г., необходимо вручную изменить готовности к установке версии для обеспечения совместимости со всеми версиями Visual Studio 2017 г.  Это так, как конструктор будет вставьте минимальный номер версии в качестве текущей версией Visual Studio (например, 15.0.26208.0).  Тем не менее, поскольку другие пользователи могут быть более ранней версии, необходимо вручную изменить ее, чтобы 15.0.

На этом этапе файла манифеста должен выглядеть примерно так:

![Пример предварительные требования](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Изменение файла проекта (myproject.csproj)

Настоятельно рекомендуется иметь ссылку на измененный .csproj, открытые во время выполнения этого шага.  Несколько примеров можно найти [здесь](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  Выделите какие-либо примеры расширяемости CSPROJ-файл для ссылки и выполните следующие действия:

* Перейдите в каталог проекта в проводнике.
* Откройте файл myproject.csproj в текстовом редакторе.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Обновление MinimumVisualStudioVersion

* Значение минимального visual studio версии `$(VisualStudioVersion)` и добавьте условный оператор для него.  Добавьте эти теги, если они не существуют.  Убедитесь, что заданы теги, как показано ниже:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Добавить свойство VsixType

* Добавьте следующий тег `<VsixType>v3</VsixType>` группу свойств.

>**Примечание:** рекомендуется добавить ниже `<OutputType></OutputType>` тег.

### <a name="3-add-the-debugging-properties"></a>3. Добавление свойства отладки

* Добавьте следующую группу свойств:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Удалите все экземпляры следующих из CSPROJ-файл и любые. csproj.user файлов:

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Добавление условий импортов средства построения

* Добавьте дополнительные условные инструкции `<import>` тегов, содержащих Microsoft.VSSDK.BuildTools ссылки.  Это можно сделать, вставив `'$(VisualStudioVersion)' != '14.0' And` с передней стороны оператора условия.  Эти инструкции будут отображаться в колонтитулы csproj-файле.

Пример:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Добавьте дополнительные условные инструкции `<import>` тегов, имеющих Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  Это можно сделать, вставив `'$(VisualStudioVersion)' == '14.0' And` с передней стороны оператора условия. Эти инструкции будут отображаться в колонтитулы csproj-файле.

Пример:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Добавьте дополнительные условные инструкции `<Error>` тегов, содержащих Microsoft.VSSDK.BuildTools ссылки.  Это можно сделать, вставив `'$(VisualStudioVersion)' != '14.0' And` с передней стороны оператора условия. Эти инструкции будут отображаться в нижнем колонтитуле csproj-файле.

Пример:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Добавьте дополнительные условные инструкции `<Error>` тегов, имеющих Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  Это можно сделать, вставив `'$(VisualStudioVersion)' == '14.0' And` с передней стороны оператора условия. Эти инструкции будут отображаться в нижнем колонтитуле csproj-файле.

Пример:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Сохраните csproj-файл и закройте его.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Тестирование устанавливает расширения в Visual Studio 2015 и Visual Studio 2017 г.

На этом этапе проект должен быть готов для построения VSIXv3, который можно установить в Visual Studio 2015 и Visual Studio 2017 г.

* Откройте проект в Visual Studio 2015
* Построение проекта и убедитесь в выходные данные, правильно ли выполняется сборка VSIX
* Перейдите в каталог проекта
* Откройте -> ячейки папка отладки
* Дважды щелкните VSIX-файл и установить расширение на Visual Studio 2015 и Visual Studio 2017 г.
* Убедитесь, вы увидите расширения в Сервис -> расширения и обновления в разделе «Установка».
* Попытка выполнения, использование расширения, чтобы проверить, что он работает

![Поиск расширение VSIX](media/finding-a-VSIX-example.png)

>**Примечание:** зависание проекта с force сообщение «Открытие файла», завершите работу Visual Studio перейдите в каталог проекта, Показать скрытые папки и удалите папку удаляйте.
