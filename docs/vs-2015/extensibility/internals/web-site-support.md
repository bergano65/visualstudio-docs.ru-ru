---
title: Поддержка веб-сайтов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1a96504783de466551c6fb9d055b95ba38df760
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687694"
---
# <a name="web-site-support"></a>Поддержка веб-сайтов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Система проектов веб-сайтов — это система проектов, которая создает веб-проекты. Веб-проекты, в свою очередь, создают веб-приложения. Проект веб-сайта создает один исполняемый файл для каждой веб-страницы, имеющей связанный код. Дополнительные исполняемые файлы создаются из файлов исходного кода в папке/App_Code.  
  
 Системы проектов веб-сайтов создаются путем добавления шаблонов и атрибутов регистрации в существующую систему проектов. Один из этих атрибутов выбирает поставщик IntelliSense для языка. Реализация поставщика IntelliSense обрабатывает ссылки и вызывает компилятор языка при запросе смарт-страницы, которая не кэшируется.  
  
 Компилятор языка, используемый для компиляции веб-страниц, должен быть зарегистрирован в [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] . Можно использовать [ \<compiler> элемент](https://msdn.microsoft.com/library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) в файле Web.config для регистрации компилятора, как показано в следующем примере:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>в этом разделе  
 [Шаблоны поддержки веб-сайтов](../../extensibility/internals/web-site-support-templates.md)  
 Список шаблонов, которые можно использовать для создания новых проектов веб-сайтов и связанных элементов.  
  
 [Атрибуты поддержки веб-сайтов](../../extensibility/internals/web-site-support-attributes.md)  
 Представляет атрибуты регистрации, соединяющие проект веб-сайта с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] .  
  
## <a name="related-sections"></a>См. также  
 [Веб-проекты](../../extensibility/internals/web-projects.md)  
 Содержит обзор двух типов веб-проектов, проектов веб-сайтов и проектов веб-приложений.
