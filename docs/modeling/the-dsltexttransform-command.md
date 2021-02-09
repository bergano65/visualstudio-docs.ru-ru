---
title: Команда DslTextTransform
description: Узнайте, что Дслтексттрансформ. cmd — это сценарий, который вызывает TextTransform.exe и запускает его с общими параметрами.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f51d1a5cbefc3c2cf60559075a9c9a299664ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924501"
---
# <a name="the-dsltexttransform-command"></a>Команда DslTextTransform
Дслтексттрансформ. cmd — это скрипт, который вызывает TextTransform.exe и запускает его с общими параметрами. Дслтексттрансформатион. cmd можно использовать для автоматизации сборки проектов в ночное время [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] . Дополнительные сведения см. [в разделе Создание файлов с помощью служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 Дслтексттрансформ. cmd находится в следующем каталоге:

 **\<Visual Studio SDK Installation Path>\висуалстудиоинтегратион\тулс\бин**

 Можно указать следующие аргументы в качестве входных данных для Дслтексттрансформ. cmd:

- Выходной каталог проекта модели предметной области.

- Выходной каталог проекта определения конструктора.

- Расположение файла текстового шаблона.

  Дслтексттрансформ. cmd обрабатывает указанный файл текстового шаблона с помощью процессоров директив по умолчанию и сборок. При создании пользовательских обработчиков директив можно создать собственный пакетный файл, который вызывает TextTransform.exe. В этом пакетном файле можно указать сборки и связанные с ними обработчики пользовательских директив.
