---
title: Команда DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89d83da450014ebf29e2882438d27f9284c9bbbb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55939038"
---
# <a name="the-dsltexttransform-command"></a>Команда DslTextTransform
DslTextTransform.cmd — это сценарий, который вызывает TextTransform.exe и запускает его с помощью общих параметров. DslTextTransformation.cmd можно использовать для автоматизации Ночные построения вашей [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] проектов. Дополнительные сведения см. в разделе [Создание файлов с помощью служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd находится в следующем каталоге:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 Можно указать следующие аргументы в качестве входных данных для DslTextTransform.cmd:

- Выходной каталог проекта модели домена.

- Выходной каталог проекта, определение конструктора.

- Расположение текстового файла шаблона.

  DslTextTransform.cmd обрабатывает указанный текстовый файл шаблона, используя процессоры директив по умолчанию и сборки. Если вы создаете пользовательские процессоры директив, можно создать собственный пакетный файл, который вызывает TextTransform.exe. В этом пакетном файле можно указать сборки и связанные пользовательские процессоры директив.