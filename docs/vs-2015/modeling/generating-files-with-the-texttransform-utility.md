---
title: Создание файлов с помощью служебной программы TextTransform | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 069f7f5ef2c579c10c1ee7c19989c79ce3ad63bf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573392"
---
# <a name="generating-files-with-the-texttransform-utility"></a>Создание файлов с помощью служебной программы TextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Создание файлов с помощью служебной программы TextTransform](https://docs.microsoft.com/visualstudio/modeling/generating-files-with-the-texttransform-utility).  
  
TextTransform.exe является средством командной строки, которое можно использовать для преобразования текстового шаблона. При вызове TextTransform.exe, указываются имя файла текстового шаблона как аргумент. TextTransform.exe вызывает обработчик преобразования текста и обрабатывает текстовый шаблон. TextTransform.exe обычно вызывается из скриптов. Тем не менее это не обычно не требуется, так как можно выполнять преобразование текста в Visual Studio или в процессе сборки.  
  
> [!NOTE]
>  Если вы хотите выполнить преобразование текста в процессе сборки, рассмотрите возможность использования задачи преобразования текста MSBuild. Дополнительные сведения см. в разделе [создание кода в процессе построения](../modeling/code-generation-in-a-build-process.md). В компьютере, на котором [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] установлен, можно также написать приложение, или [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] расширение, которое может выполнять преобразование текстовых шаблонов. Дополнительные сведения см. в разделе [обработки текстовых шаблонов с помощью пользовательского хост-](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 TextTransform.exe находится в следующем каталоге:  
  
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
|**-out** \<имя файла >|Файл, куда будут записываться выходные данные преобразования.|  
|**-r** \<сборки >|Сборка, используемая для компиляции и выполнении шаблона текста.|  
|**-u** \<пространства имен >|Пространство имен, который используется для компиляции шаблона.|  
|**-I** \<includedirectory>|Каталог, содержащий текстовые шаблоны, включенные в указанный текстовый шаблон.|  
|**-P** \<referencepath >|Каталог поиска для сборки, указанные в текстовом шаблоне или с помощью **- r** параметр.<br /><br /> Например чтобы включить сборки, используемые для Visual Studio API, используйте<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName >!\< имя_класса >! \<assemblyName&#124;codeBase >|Имя, полное имя типа и сборки процессора директив, который может использоваться для обработки пользовательских директив в текстовый шаблон.|  
|**-** [processorName]! [directiveName]! \<Имя_параметра >! \<parameterValue >|Укажите значение параметра для процессора директив. Если указать только имя параметра и значение параметра будут доступны все процессоры директив. Если указать процессор директив, параметр будет доступен только для указанного процессора. Если указать имя директивы, параметр будет доступен только в том случае, когда обрабатывается конкретной директивы.<br /><br />  В текстовом шаблоне, включают `hostspecific` в директиве template и вызвать сообщение на `this.Host`. Пример:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Всегда введите "!" помечает, даже если не указан необязательный процессора и имен директивы. Пример:<br /><br /> `-a !!param!value`|  
|**-h**|Содержит справочную информацию.|  
  
## <a name="related-topics"></a>См. также  
  
|Задача|Раздел|  
|----------|-----------|  
|Создание файлов в решении [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|Написание процессоров директив для преобразования собственных источников данных.|[Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md)|  
|Напишите текст шаблонов узла, который позволяет вызывать текстовые шаблоны из собственного приложения.|[Обработка текстовых шаблонов с помощью пользовательского хост-класса](../modeling/processing-text-templates-by-using-a-custom-host.md)|



