---
title: Типы файлов проектов и решений
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3786d6f38e4f87aa05a51b0a6112613bda65e56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947603"
---
# <a name="project-and-solution-file-types"></a>Типы файлов проектов и решений

Visual Studio поддерживает многие типы файлов. В определенной установке поддерживаемые типы файлы определяются установленными компонентами. В этом разделе перечислены типы файлов решений и проектов, которые поддерживаются в некоторых типичных установках.

## <a name="solution-files-sln-and-suo"></a>Файлы решений (SLN и SUO)

В Visual Studio используются два типа файлов (SLN и SUO) для хранения параметров, связанных с решениями. Эти файлы, которые называют файлами решений, предоставляют Обозревателю решений информацию, необходимую для отображения графического интерфейса, используемого для управления файлами.

|Расширение|name|Описание:|
|---------------|----------|-----------------|
|.SLN|Решение Visual Studio|Организует проекты, элементы проектов и решений в решение.|
|SUO|Параметры пользователя решения|Отслеживает настройки на уровне пользователя в Visual Studio, такие как точки останова.|

## <a name="project-files"></a>Файлы проекта

Проекты могут содержать файлы множества различных типов. Например, файлы кода на C# имеют расширение **CS**, а файлы C++ — расширение **CPP**. Ресурсы хранятся в файлах **RESX**, а код XAML — в файлах **XAML**. Файлы [app.config](../../ide/managing-application-settings-dotnet.md) содержат сведения о приложении, которые не следует включать в код приложения,&mdash;например строки подключения.

Дополнительные сведения о типах файлов в проекте C++ см. в разделе [Типы файлов, создаваемых для проектов Visual C++](/cpp/ide/file-types-created-for-visual-cpp-projects).

## <a name="see-also"></a>См. также

- [Решения и проекты](../../ide/solutions-and-projects-in-visual-studio.md)