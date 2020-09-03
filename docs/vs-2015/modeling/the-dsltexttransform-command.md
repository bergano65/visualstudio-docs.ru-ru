---
title: Команда Дслтексттрансформ | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 599bf14a3d37fbd6bdff111f79e658f44624792b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658467"
---
# <a name="the-dsltexttransform-command"></a>Команда DslTextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Дслтексттрансформ. cmd — это скрипт, который вызывает TextTransform.exe и запускает его с общими параметрами. Дслтексттрансформатион. cmd можно использовать для автоматизации сборки проектов в ночное время [!INCLUDE[dsl](../includes/dsl-md.md)] . Дополнительные сведения см. [в разделе Создание файлов с помощью служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 Дслтексттрансформ. cmd находится в следующем каталоге:

 **\<Visual Studio SDK Installation Path>\висуалстудиоинтегратион\тулс\бин**

 Можно указать следующие аргументы в качестве входных данных для Дслтексттрансформ. cmd:

- Выходной каталог проекта модели предметной области.

- Выходной каталог проекта определения конструктора.

- Расположение файла текстового шаблона.

  Дслтексттрансформ. cmd обрабатывает указанный файл текстового шаблона с помощью процессоров директив по умолчанию и сборок. При создании пользовательских обработчиков директив можно создать собственный пакетный файл, который вызывает TextTransform.exe. В этом пакетном файле можно указать сборки и связанные с ними обработчики пользовательских директив.
