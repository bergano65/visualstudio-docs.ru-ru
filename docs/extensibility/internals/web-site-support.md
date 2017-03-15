---
title: "Поддержка веб-сайта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 636cbee868bb53be2d0ef85bd309459570eb84c0
ms.lasthandoff: 02/22/2017

---
# <a name="web-site-support"></a>Поддержка веб-сайтов
Система проектов веб-сайта — это система, создающий веб-проектов. Веб-проектов, в свою очередь, создавать веб-приложения. Проект веб-узла создает один исполняемый файл для каждой веб-страницы, который связан код. Дополнительные исполняемые файлы создаются из файлов исходного кода в папке/App_Code.  
  
 Веб-сайт проекта системы создаются путем добавления шаблоны и атрибуты регистрации в существующей системе проекта. Один из этих атрибутов выбирает поставщика IntelliSense для языка. Реализация поставщика IntelliSense обрабатывает ссылки и вызывает компилятор языка, при запросе смарт-веб-страницы, не кэшируется.  
  
 Компилятор языка, который используется для компиляции веб-страницы должен быть зарегистрирован с [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]. Можно использовать [ \<компилятора настроек элемент](http://msdn.microsoft.com/Library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) в файле Web.config, чтобы зарегистрировать компилятор, как показано в следующем примере:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>Содержание  
 [Шаблоны веб-сайта поддержки](../../extensibility/internals/web-site-support-templates.md)  
 Список шаблонов, которые можно использовать для создания новых проектов веб-сайтов и связанных элементов.  
  
 [Атрибуты веб-сайта поддержки](../../extensibility/internals/web-site-support-attributes.md)  
 Представляет атрибуты регистрации, проект веб-сайта для подключения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].  
  
## <a name="related-sections"></a>Связанные разделы  
 [Веб-проекты](../../extensibility/internals/web-projects.md)  
 Представляет обзор двух типов веб-проектов, проектов веб-сайтов и проектов веб-приложений.
