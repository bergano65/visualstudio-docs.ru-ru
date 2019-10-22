---
title: Создание файлов с помощью служебной программы TextTransform | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18776795fdf693c855edd3f629d674089daaaebd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666093"
---
# <a name="generating-files-with-the-texttransform-utility"></a>Создание файлов с помощью служебной программы TextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TextTransform. exe — это программа командной строки, которую можно использовать для преобразования текстового шаблона. При вызове TextTransform. exe в качестве аргумента указывается имя файла текстового шаблона. TextTransform. exe вызывает модуль преобразования текста и обрабатывает текстовый шаблон. TextTransform. exe обычно вызывается из скриптов. Однако обычно это не требуется, так как можно выполнить преобразование текста в Visual Studio или в процессе сборки.

> [!NOTE]
> Если вы хотите выполнить преобразование текста как часть процесса сборки, рассмотрите возможность использования задачи преобразования текста MSBuild. Дополнительные сведения см. [в разделе Создание кода в процессе сборки](../modeling/code-generation-in-a-build-process.md). На компьютере, на котором установлена [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], можно также написать приложение или [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] расширение, которое может преобразовывать текстовые шаблоны. Дополнительные сведения см. [в разделе Обработка текстовых шаблонов с помощью пользовательского узла](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform. exe находится в следующем каталоге:

 **\Program Files\Common Files\Microsoft Shared\TextTemplating\11.0**

## <a name="syntax"></a>Синтаксис

```
TextTransform [<options>] <templateName>
```

#### <a name="parameters"></a>Параметры

|**Аргумент**|**Описание**|
|------------------|---------------------|
|`templateName`|Определяет имя файла шаблона, который требуется преобразовать.|

|**Параметр**|**Описание**|
|----------------|---------------------|
|**-out** \<filename >|Файл, в который записывается выходные данные преобразования.|
|**-r** \<assembly >|Сборка, используемая для компиляции и выполнения текстового шаблона.|
|**-u** \<namespace >|Пространство имен, используемое для компиляции шаблона.|
|**-I** \<includedirectory >|Каталог, содержащий текстовые шаблоны, содержащиеся в указанном текстовом шаблоне.|
|**-P** \<referencepath >|Каталог для поиска сборок, указанных в текстовом шаблоне, или для использования параметра **-r** .<br /><br /> Например, чтобы включить сборки, используемые для Visual Studio API, используйте<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName >! \<className >! \<assemblyName&#124;CodeBase >|Имя, полное имя типа и сборка обработчика директив, которые могут использоваться для обработки пользовательских директив в текстовом шаблоне.|
|**-a** [процессорнаме]! [Директивенаме]! \<parameterName >! \<parameterValue >|Укажите значение параметра для обработчика директив. Если указать только имя и значение параметра, параметр будет доступен для всех процессоров директив. Если указан процессор директив, параметр доступен только для указанного процессора. Если указать имя директивы, параметр будет доступен только при обработке указанной директивы.<br /><br />  В текстовом шаблоне включите `hostspecific` в директиву template и вызовите сообщение в `this.Host`. Пример:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`<br /><br /> Всегда вводите метки "!", даже если опустить необязательные имена процессора и директивы. Пример:<br /><br /> `-a !!param!value`|
|**-h**|Предоставляет справку.|

## <a name="related-topics"></a>См. также

|Задача|Раздел|
|----------|-----------|
|Создание файлов в решении [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Написание процессоров директив для преобразования собственных источников данных.|[Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md)|
|Напишите узел текстовых шаблонов, который позволяет вызывать текстовые шаблоны из собственного приложения.|[Обработка текстовых шаблонов с помощью пользовательского хост-класса](../modeling/processing-text-templates-by-using-a-custom-host.md)|
