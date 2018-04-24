---
title: Общие свойства проекта (Android C++ Makefile) | Документы Майкрософт
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.ConfigurationType
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: cfc1655adbd9377f1aeeec60afc799f342b4498d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="general-project-properties-android-c-makefile"></a>Общие свойства проекта (Android C++ Makefile)

Свойство. | Описание: | Варианты
--- | ---| ---
Выходной каталог | Указывает относительный путь к выходному каталогу файлов; может включать в себя переменные среды.
Промежуточный каталог | Указывает относительный путь к промежуточному каталогу файлов; может включать в себя переменные среды.
Файл журнала сборки | Определяет файл журнала сборки, в который будет вестись запись, если ведение журнала включено.
Тип конфигурации | Определяет тип выходных данных, создаваемых этой конфигурацией. | **Динамическая библиотека (.so)** — динамическая библиотека (.so)<br>**Статическая библиотека (.a)** — статическая библиотека (.a)<br>**Служебная программа** — служебная программа<br>**Makefile** — файл Makefile<br>
