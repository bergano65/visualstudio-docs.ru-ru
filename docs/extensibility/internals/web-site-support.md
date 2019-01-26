---
title: Поддержка веб-сайтов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a84b59085e2850a7c889e3468788fb8ef23414ca
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959918"
---
# <a name="web-site-support"></a>Поддержка веб-сайтов
Систему проектов веб-сайта — это система, создающий веб-проектов. Веб-проектов, в свою очередь, создайте веб-приложений. Проект веб-сайта создает один исполняемый файл для каждого веб-страницы, который связан код. Дополнительные исполняемые файлы создаются из файлов исходного кода в папке/App_Code.  
  
 Системы проектов веб-сайте создаются путем добавления шаблоны и атрибуты регистрации в существующей системе проекта. Один из этих атрибутов выбирает поставщика IntelliSense для языка. Реализация поставщика IntelliSense обрабатывает ссылки и вызывает компилятор языка, когда запрашивается смарт-веб-страницы, не кэшируется.  
  
 Компилятор языка, используемый для компиляции веб-страниц, которые должны быть зарегистрированы в [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]. Можно использовать [ \<компилятор > элемент](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) в файле Web.config, чтобы зарегистрировать компилятор, как показано в следующем примере:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>В этом разделе  
 [Шаблоны поддержки веб-сайтов](../../extensibility/internals/web-site-support-templates.md)  
 Список шаблонов, которые можно использовать для создания новых проектов веб-сайтов и связанных элементах.  
  
 [Атрибуты поддержки веб-сайтов](../../extensibility/internals/web-site-support-attributes.md)  
 Представляет атрибуты регистрации, которые подключаются проекте веб-сайта для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].  
  
## <a name="related-sections"></a>Связанные разделы  
 [Веб-проекты](../../extensibility/internals/web-projects.md)  
 Представляет обзор двух типов веб-проектов, проектов веб-сайтов и проектов веб-приложений.