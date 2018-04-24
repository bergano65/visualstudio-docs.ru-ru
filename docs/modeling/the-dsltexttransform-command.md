---
title: Команда DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a3605dd3d6cd7615a2afd4dba18bf2f7bed994f4
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="the-dsltexttransform-command"></a>Команда DslTextTransform
DslTextTransform.cmd — это сценарий, который вызывает TextTransform.exe и запускает его с помощью общих параметров. DslTextTransformation.cmd можно использовать для автоматизации Ночные построения из вашего [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] проектов. Дополнительные сведения см. в разделе [создания файлов с помощью служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd находится в следующем каталоге:

 **\<Путь установки пакета SDK для Visual Studio > \VisualStudioIntegration\Tools\Bin**

 В качестве входного для DslTextTransform.cmd можно указать следующие аргументы:

-   Выходной каталог проекта модели домена.

-   Выходной каталог проекта, определение конструктора.

-   Расположение текстового файла шаблона.

 DslTextTransform.cmd обрабатывает указанный текстовый файл шаблона, с помощью процессоров директив по умолчанию и сборки. При создании пользовательского процессора директив, можно создать собственные пакетный файл, который вызывает TextTransform.exe. В этом пакетном файле можно указать сборки и связанные пользовательские процессоры директив.