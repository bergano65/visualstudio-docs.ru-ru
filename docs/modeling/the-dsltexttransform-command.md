---
title: Команда DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a303fc3ddb880402e3f998b2360122f6f056b757
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605933"
---
# <a name="the-dsltexttransform-command"></a>Команда DslTextTransform
Дслтексттрансформ. cmd — это сценарий, который вызывает TextTransform. exe и запускает его с общими параметрами. Дслтексттрансформатион. cmd можно использовать для автоматизации сборки [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] проектов в ночное время. Дополнительные сведения см. [в разделе Создание файлов с помощью служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 Дслтексттрансформ. cmd находится в следующем каталоге:

 **Путь установки пакета SDK для \<Visual Studio > \Висуалстудиоинтегратион\тулс\бин**

 Можно указать следующие аргументы в качестве входных данных для Дслтексттрансформ. cmd:

- Выходной каталог проекта модели предметной области.

- Выходной каталог проекта определения конструктора.

- Расположение файла текстового шаблона.

  Дслтексттрансформ. cmd обрабатывает указанный файл текстового шаблона с помощью процессоров директив по умолчанию и сборок. При создании пользовательских обработчиков директив можно создать собственный пакетный файл, который вызывает TextTransform. exe. В этом пакетном файле можно указать сборки и связанные с ними обработчики пользовательских директив.