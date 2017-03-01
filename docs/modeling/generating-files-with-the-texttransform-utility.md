---
title: "Создание файлов с помощью служебной программы TextTransform | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 41
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7d54fba9b16b87122b78ec6157abdbf2a8aface1
ms.lasthandoff: 02/22/2017

---
# <a name="generating-files-with-the-texttransform-utility"></a>Создание файлов с помощью служебной программы TextTransform
TextTransform.exe является средством командной строки, который можно использовать для преобразования текстового шаблона. При вызове TextTransform.exe указываются имя файла текстового шаблона в качестве аргумента. TextTransform.exe вызывает обработчик преобразования текста и обрабатывает шаблон текста. TextTransform.exe обычно вызывается из скриптов. Тем не менее не обычно не требуется, поскольку можно выполнить преобразование текста в Visual Studio или в процессе построения.  
  
> [!NOTE]
>  Если вы хотите выполнить преобразование текста в рамках процесса построения, рассмотрите возможность использования задачи преобразования текста MSBuild. Дополнительные сведения см. в разделе [создание кода в процессе построения](../modeling/code-generation-in-a-build-process.md). На компьютере, на котором [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] установлен, можно также написать приложение или [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] расширение, которое можно преобразования текстовых шаблонов. Дополнительные сведения см. в разделе [обработки текстовых шаблонов с помощью пользовательского хост-класса](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 TextTransform.exe находится в следующем каталоге:  
  
 **Создаваемую Shared\TextTemplating\11.0 \Program Files\Common**  
  
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
|**-out** \<имя файла настроек|Файл, в который записывается результат преобразования.|  
|**-r** \<сборки настроек|Сборка, используемая для компиляции и выполнения шаблона текста.|  
|**-u** \<имен настроек|Пространство имен, который используется для компиляции шаблона.|  
|**-I** \<includedirectory настроек|Каталог, содержащий текстовые шаблоны, включенные в указанный текстовый шаблон.|  
|**-P** \<referencepath настроек|Указывает каталог поиска для сборок, указанных в текстовом шаблоне или с помощью **- r** параметр.<br /><br /> Например чтобы включить сборки, используемые для Visual Studio API, используйте<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName настроек!\< className настроек! \<имя_сборки | codeBase настроек|Имя, полное имя типа и сборка процессора директив, который может использоваться для обработки пользовательских директивы в текстовом шаблоне.|  
|**-** [processorName]. [ directiveName]! \<parameterName настроек! \<parameterValue настроек|Укажите значение параметра для процессора директив. Если указать только имя параметра и значение параметра будут доступны все процессоры директив. При указании процессор директив, то параметр будет доступен только для указанного процессора. При указании имени директивы, то параметр будет доступен только при обработке указанной директивы.<br /><br /> Для доступа к значения параметра процессора директив или текстовый шаблон, используйте <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A>.</xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A> В текстовом шаблоне включают `hostspecific` в директиве шаблона и вызывать сообщения на `this.Host`. Пример:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Всегда вводить '!' помечает, даже если не указан необязательный процессора и имена директив. Например:<br /><br /> `-a !!param!value`|  
|**-h**|Содержит справочную информацию.|  
  
## <a name="related-topics"></a>См. также  
  
|Задача|Раздел|  
|----------|-----------|  
|Создание файлов в решении [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|[Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|Написание процессоров директив для преобразования собственных источников данных.|[Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md)|  
|Написать текст шаблонов узла, который позволяет вызывать текстовые шаблоны из собственного приложения.|[Обработка текстовых шаблонов с помощью пользовательского хост-класса](../modeling/processing-text-templates-by-using-a-custom-host.md)|
