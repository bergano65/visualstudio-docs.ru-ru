---
title: Создание файлов с помощью служебной программы TextTransform
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f224419cd92b760d71045859a13887a83115b987
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606091"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Создание файлов с помощью служебной программы TextTransform

TextTransform.exe является средством командной строки, которое можно использовать для преобразования текстового шаблона. При вызове TextTransform.exe, указываются имя файла текстового шаблона как аргумент. TextTransform.exe вызывает обработчик преобразования текста и обрабатывает текстовый шаблон. TextTransform.exe обычно вызывается из скриптов. Тем не менее это не обычно не требуется, так как можно выполнять преобразование текста в Visual Studio или в процессе сборки.

> [!NOTE]
> Если вы хотите выполнить преобразование текста в процессе сборки, рассмотрите возможность использования задачи преобразования текста MSBuild. Дополнительные сведения см. в разделе [создание кода в процессе построения](../modeling/code-generation-in-a-build-process.md). На компьютере, на котором установлена Visual Studio можно также написать приложение или расширение Visual Studio, которое может выполнять преобразование текстовых шаблонов. Дополнительные сведения см. в разделе [обработки текстовых шаблонов с помощью пользовательского хост-](../modeling/processing-text-templates-by-using-a-custom-host.md).

TextTransform.exe находится в следующем каталоге:
 
::: moniker range=">=vs-2019"

**\Program Files (x86) \Microsoft Visual Studio\2019\Professional\Common7\IDE**

для выпуска Professional Edition или

**\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

для выпуска Enterprise Edition.

::: moniker-end
 
::: moniker range="vs-2017"

**\Program файлы (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

для выпуска Professional Edition или

**\Program файлы (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

для выпуска Enterprise Edition.

В предыдущих версиях Visual Studio этот файл находится в следующем расположении:

**\Program файлы (x86) \Common Files\Microsoft Shared\TextTemplating\{версии}**

где {версия} зависит от установленной предыдущей версии.

::: moniker-end

## <a name="syntax"></a>Синтаксис

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Параметры

|**Аргумент**|**Описание**|
|-|-|
|`templateName`|Определяет имя файла шаблона, который требуется преобразовать.|

|**Параметр**|**Описание**|
|-|-|
|**-out** \<имя файла >|Файл, куда будут записываться выходные данные преобразования.|
|**-r** \<сборки >|Сборка, используемая для компиляции и выполнении шаблона текста.|
|**-u** \<пространства имен >|Пространство имен, который используется для компиляции шаблона.|
|**-I** \<includedirectory>|Каталог, содержащий текстовые шаблоны, включенные в указанный текстовый шаблон.|
|**-P** \<referencepath >|Каталог поиска для сборки, указанные в текстовом шаблоне или с помощью **- r** параметр.<br /><br /> Например чтобы включить сборки, используемые для Visual Studio API, используйте<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName >!\< имя_класса >! \<assemblyName&#124;codeBase >|Имя, полное имя типа и сборки процессора директив, который может использоваться для обработки пользовательских директив в текстовый шаблон.|
|**-** [processorName]! [directiveName]! \<Имя_параметра >! \<parameterValue >|Укажите значение параметра для процессора директив. Если указать только имя параметра и значение параметра будут доступны все процессоры директив. Если указать процессор директив, параметр будет доступен только для указанного процессора. Если указать имя директивы, параметр будет доступен только в том случае, когда обрабатывается конкретной директивы.<br /><br /> Чтобы получить значения параметров из процессора директив или текстового шаблона, используйте [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). В текстовом шаблоне, включают `hostspecific` в директиве template и вызвать сообщение на `this.Host`. Пример:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Всегда введите "!" помечает, даже если не указан необязательный процессора и имен директивы. Пример:<br /><br /> `-a !!param!value`|
|**-h**|Содержит справочную информацию.|

## <a name="related-topics"></a>См. также

|Задача|Раздел|
|-|-|
|Создание файлов в решении Visual Studio.|[Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Написание процессоров директив для преобразования собственных источников данных.|[Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md)|
|Напишите текст шаблонов узла, который позволяет вызывать текстовые шаблоны из собственного приложения.|[Обработка текстовых шаблонов с помощью пользовательского хост-класса](../modeling/processing-text-templates-by-using-a-custom-host.md)|
