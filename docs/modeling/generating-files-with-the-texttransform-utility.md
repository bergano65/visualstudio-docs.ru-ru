---
title: Создание файлов с помощью служебной программы TextTransform в Visual Studio | Документы Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 930d8982f8d34bae2870276623ae2d71a24372d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="generate-files-with-the-texttransform-utility"></a>Создание файлов с помощью служебной программы TextTransform

TextTransform.exe является средством командной строки, которое можно использовать для преобразования текстового шаблона. При вызове TextTransform.exe указываются имя файла текстового шаблона как аргумент. TextTransform.exe вызывает обработчик преобразования текста и обрабатывает текстового шаблона. TextTransform.exe обычно вызывается из скриптов. Тем не менее это не обычно не требуется, поскольку выполняется преобразование текста в Visual Studio или в процессе построения.

> [!NOTE]
> Если вы хотите выполнить преобразование текста в рамках процесса построения, рассмотрите возможность использования задачи преобразования текста MSBuild. Дополнительные сведения см. в разделе [создание кода в процессе сборки](../modeling/code-generation-in-a-build-process.md). В компьютере, на котором [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] установлен, можно также написать приложение или [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] расширение, которое можно преобразования текстовых шаблонов. Дополнительные сведения см. в разделе [обработка текстовых шаблонов с помощью пользовательского хост-класса](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform.exe находится в следующем каталоге:

 **\Program файлы (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

для выпуска Professional или

 **\Program файлы (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

 для выпуска Enterprise edition.

В предыдущих версиях Visual Studio этот файл находится в следующем расположении:

**Файлы (x86) \Program \Common Files\Microsoft Shared\TextTemplating\{версии}**

где {version} зависит от установленной предыдущей версии.

## <a name="syntax"></a>Синтаксис

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Параметры

|**Аргумент**|**Описание**|
|------------------|---------------------|
|`templateName`|Определяет имя файла шаблона, который требуется преобразовать.|

|**Параметр**|**Описание**|
|----------------|---------------------|
|**-out** \<имя файла >|Файл, в который записывается выходные данные преобразования.|
|**-r** \<сборки >|Сборка, используемая для компиляции и выполнения шаблона текста.|
|**-u** \<пространство имен >|Пространство имен, которое используется для компиляции шаблона.|
|**-I** \<includedirectory>|Каталог, содержащий текстовые шаблоны, включенные в указанный текстовый шаблон.|
|**-P** \<referencepath >|Указывает каталог поиска для сборок, указанных в текстовом шаблоне или с помощью **- r** параметр.<br /><br /> Например чтобы включить сборки, используемые для Visual Studio API, используйте<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName >!\< имя_класса >! \<assemblyName&#124;codeBase >|Имя, полное имя типа и сборка процессора директив, который может использоваться для обработки пользовательских директивы в текстовом шаблоне.|
|**-** [processorName]! [directiveName]! \<Имя_параметра >! \<parameterValue >|Укажите значение параметра для процессора директив. Если указать только имя параметра и значение параметра будет доступен для всех процессоров директив. При указании процессора директив параметр доступен только для указанного процессора. При указании имени директивы, то параметр будет доступен только при обработке указанной директивы.<br /><br /> Для доступа к значения параметров из процессора директив или текстовый шаблон, используйте [ITextTemplatingEngineHost.ResolveParameterValue](https://msdn.microsoft.com/library/microsoft.visualstudio.texttemplating.itexttemplatingenginehost.resolveparametervalue.aspx). В текстовом шаблоне включают `hostspecific` в директиве шаблона и вызвать сообщение на `this.Host`. Пример:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Всегда введите "!" помечает, даже если не указан необязательный процессора и имен директивы. Пример:<br /><br /> `-a !!param!value`|
|**-h**|Предоставляет справку.|

## <a name="related-topics"></a>См. также

|Задача|Раздел|
|----------|-----------|
|Создание файлов в решении [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|[Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Написание процессоров директив для преобразования собственных источников данных.|[Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md)|
|Запись шаблонов узла текста, который позволяет вызывать текстовые шаблоны из собственного приложения.|[Обработка текстовых шаблонов с помощью пользовательского хост-класса](../modeling/processing-text-templates-by-using-a-custom-host.md)|