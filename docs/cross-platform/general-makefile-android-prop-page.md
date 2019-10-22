---
title: Общие свойства проекта (Android C++ Makefile) | Документы Майкрософт
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.ConfigurationType
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: b7fa1b91951e7a3fb145cc26275016037d1b5f2b
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950581"
---
# <a name="general-project-properties-android-c-makefile"></a>Общие свойства проекта (Android C++ Makefile)

Свойство. | ОПИСАНИЕ | Варианты
--- | ---| ---
Выходной каталог | Указывает относительный путь к выходному каталогу файлов; может включать в себя переменные среды.
Промежуточный каталог | Указывает относительный путь к промежуточному каталогу файлов; может включать в себя переменные среды.
Файл журнала сборки | Определяет файл журнала сборки, в который будет вестись запись, если ведение журнала включено.
Тип конфигурации | Определяет тип выходных данных, создаваемых этой конфигурацией. | **Динамическая библиотека (.so)**  — динамическая библиотека ( *.so*)<br>**Статическая библиотека (.a)** — статическая библиотека ( *.a*)<br>**Служебная программа** — служебная программа<br>**Makefile** — файл Makefile<br>
