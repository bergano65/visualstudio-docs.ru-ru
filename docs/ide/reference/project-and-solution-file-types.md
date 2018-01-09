---
title: "Типы файлов проектов и решений | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- File Properties.CopyToOutputDirectory
- File Properties.CustomToolNamespace
- File Properties.FileName
- File Properties.FullPath
- File Properties.BuildAction
- File Properties.CustomTool
- FileProperties
helpviewer_keywords:
- .sln files
- .suo files
- file types [Visual Studio]
- file extensions [Visual Studio]
- solution files [Visual Studio]
- sln files
- suo files
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d05b7b5f1510777c758998572e78757c47148fa1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="project-and-solution-file-types"></a>Типы файлов проектов и решений

Visual Studio поддерживает многие типы файлов. В определенной установке поддерживаемые типы файлы определяются установленными компонентами. В этом разделе перечислены типы файлов решений и проектов, которые поддерживаются в некоторых типичных установках.

## <a name="solution-files-sln-and-suo"></a>Файлы решений (SLN и SUO)

В Visual Studio используются два типа файлов (SLN и SUO) для хранения параметров, связанных с решениями. Эти файлы, которые называют файлами решений, предоставляют Обозревателю решений информацию, необходимую для отображения графического интерфейса, используемого для управления файлами.

|Расширение|Имя|Описание|
|---------------|----------|-----------------|
|.SLN|Решение Visual Studio|Организует проекты, элементы проектов и решений в решение.|
|SUO|Параметры пользователя решения|Отслеживает настройки на уровне пользователя в Visual Studio, такие как точки останова.|

## <a name="project-files"></a>Файлы проекта

Проекты могут содержать файлы множества различных типов. Например, файлы кода на C# имеют расширение **CS**, а файлы C++ — расширение **CPP**. Ресурсы хранятся в файлах **RESX**, а код XAML — в файлах **XAML**. Файлы [app.config](../../ide/managing-application-settings-dotnet.md) содержат сведения о приложении, которые не следует включать в код приложения,&mdash;например строки подключения.

Дополнительные сведения о типах файлов в проектах C++ см. в статьях [Типы файлов, создаваемых для проектов Visual C++](/cpp/ide/file-types-created-for-visual-cpp-projects) и [Юникод в библиотеке Microsoft Foundation Class](/cpp/mfc/unicode-in-mfc).

## <a name="see-also"></a>См. также

[Решения и проекты](../../ide/solutions-and-projects-in-visual-studio.md)