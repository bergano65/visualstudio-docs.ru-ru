---
title: Поддержка веб-сайта Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22047ad1b0709cefa200656e61f8e0d39ace94c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703448"
---
# <a name="web-site-support"></a>Поддержка веб-сайтов
Проектная система веб-узла — это проектная система, которая создает веб-проекты. Веб-проекты, в свою очередь, создают веб-приложения. Проект веб-узла генерирует один исполняемый файл для каждой веб-страницы с соответствующим кодом. Дополнительные исполняемые файлы генерируются из файлов исходного кода в папке /App_Code.

 Системы проектов веб-узла создаются путем добавления шаблонов и атрибутов регистрации в существующую проектную систему. Один из этих атрибутов выбирает поставщика IntelliSense для языка. Реализация поставщика IntelliSense обрабатывает ссылки и вызывает компилятор языка при запросе умной веб-страницы, которая не кэшируется.

 Компилятор языка, используемый для компиляции веб-страниц, должен быть зарегистрирован [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]с . Для регистрации компилятора можно использовать [ \<компилятор>](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) Элементвай в файле Web.config, как в следующем примере:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>В этом разделе
- [Шаблоны поддержки веб-сайтов](../../extensibility/internals/web-site-support-templates.md)

 Перечисляет шаблоны, которые можно использовать для создания новых проектов веб-узлов и связанных с ними элементов.

- [Атрибуты поддержки веб-сайтов](../../extensibility/internals/web-site-support-attributes.md)

 Представляет атрибуты регистрации, которые соединяют проект веб-узла к [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].

## <a name="related-sections"></a>Связанные разделы
- [Веб-проекты](../../extensibility/internals/web-projects.md)

 Представляет обзор двух видов веб-проектов, проектов веб-узлов и проектов веб-приложений.
