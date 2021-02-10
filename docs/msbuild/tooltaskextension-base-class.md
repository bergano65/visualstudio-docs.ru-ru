---
title: Базовый класс ToolTaskExtension | Документы Майкрософт
description: Сведения о параметрах, которые базовый класс Microsoft.Build.Tasks.ToolTaskExtension добавляет к производным от него задачам.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 258ae433-f68a-49f1-b276-da20e3472e68
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7a12607a6e4f603c86e7714ff87db085d3bf3b9c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965945"
---
# <a name="tooltaskextension-base-class"></a>Базовый класс ToolTaskExtension

Многие задачи наследуют от класса <xref:Microsoft.Build.Tasks.ToolTaskExtension>, наследующего от класса <xref:Microsoft.Build.Utilities.ToolTask>, который в свою очередь наследует от класса <xref:Microsoft.Build.Utilities.Task>. Эта цепочка наследования добавляет несколько параметров в задачи, которые от них происходят. Эти параметры перечислены в настоящем документе.

## <a name="parameters"></a>Параметры

 В следующей таблице описываются параметры базовых классов.

| Параметр | Описание |
| - | - |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A> | Необязательный параметр <xref:Microsoft.Build.Framework.IBuildEngine>.<br /><br /> Задает интерфейс подсистемы сборки, доступный для задач. Подсистема сборки автоматически устанавливает этот параметр, чтобы разрешить задачам обратный вызов. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A> | Необязательный параметр <xref:Microsoft.Build.Framework.IBuildEngine2>.<br /><br /> Задает интерфейс подсистемы сборки, доступный для задач. Подсистема сборки автоматически устанавливает этот параметр, чтобы разрешить задачам обратный вызов.<br /><br /> Это свойство предусмотрено для удобства, чтобы разработчикам, наследующим из этого класса, не приходилось приводить значение из `IBuildEngine` в `IBuildEngine2`. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A> | Необязательный параметр <xref:Microsoft.Build.Framework.IBuildEngine3>.<br /><br /> Задает интерфейс подсистемы сборки, предоставляемый узлом. |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Необязательный параметр `bool`.<br /><br /> Если задано значение `true`, то задача передает **/Q** в командную строку *cmd.exe* и командная строка не копируется в stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Необязательный параметр массива `String`.<br /><br /> Массив пар переменных среды, разделенных знаками равенства. Эти переменные частично передаются в порожденный исполняемый файл, дополняя или выборочно переопределяя обычный блок среды. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Необязательный выходной параметр `Int32`, доступный только для чтения.<br /><br /> Задает код выхода, предоставляемый выполняемой командой. Если задача зарегистрировала какие-либо ошибки, но процесс имеет код выхода 0 (успешное завершение), этот параметр имеет значение -1. |
| <xref:Microsoft.Build.Utilities.Task.HostObject%2A> | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskHost>.<br /><br /> Указывает экземпляр объекта узла (может иметь значение null). Подсистема сборки задает это свойство, если интегрированная среда разработки узла связывает объект узла с этой конкретной задачей. |
| <xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A> | Необязательный параметр <xref:Microsoft.Build.Utilities.TaskLoggingHelper>, доступный только для чтения.<br /><br /> Возвращает экземпляр класса <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension>, который содержит методы ведения журнала задачи. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Необязательный параметр `bool`<br /><br /> Если он имеет значение `true`, то все сообщения, полученные в стандартном потоке ошибок, регистрируются как ошибки. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Необязательный параметр `String`.<br /><br /> Степень важности, с которой текст из стандартного выходного потока следует регистрировать в журнале. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Необязательный параметр `String`.<br /><br /> Степень важности, с которой текст из стандартного выходного потока следует регистрировать в журнале. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Виртуальный дополнительный параметр `Int32`.<br /><br /> Задает промежуток времени в миллисекундах, после которого исполняемый файл задачи прекращается. Значение по умолчанию — `Int.MaxValue`. Оно указывает, что период ожидания отсутствует. Время ожидания в миллисекундах. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Виртуальный дополнительный параметр `string`.<br /><br /> Он может реализовываться в проектах для переопределения параметра ToolName. Задачи могут переопределять его для сохранения параметра ToolName. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Необязательный параметр `string`.<br /><br /> Указывает расположение, откуда задача загружает базовый исполняемый файл. Если этот параметр не задан, задача использует путь установки пакета SDK, соответствующий версии платформы, на которой выполняется MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Необязательный параметр `bool`.<br /><br /> Если задано значение `true`, эта задача создает пакетный файл для командной строки и выполняет его с помощью командного процессора вместо непосредственного выполнения команды. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Необязательный параметр `bool`.<br /><br /> Если задано значение `true`, эта задача создает узел при выполнении его задачи. |

## <a name="see-also"></a>См. также раздел

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Задачи](../msbuild/msbuild-tasks.md)
