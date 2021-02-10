---
title: Задачи MSBuild, относящиеся к C++ | Документация Майкрософт
description: Сведения о задачах MSBuild, которые становятся доступными после установки C++ и которые MSBuild использует при компиляции кода C++.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 82ba5ad3beb8a676df23cc69184c8766bca72f77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878270"
---
# <a name="msbuild-tasks-specific-to-c"></a>Задачи MSBuild, относящиеся к C++

Задачи содержат код, который выполняется в процессе сборки. После установки C++ доступны следующие задачи, помимо тех, которые устанавливаются вместе с MSBuild. Дополнительные сведения см. в [обзоре MSBuild (C++)](/cpp/build/msbuild-visual-cpp-overview).

 Помимо общих для всех задач параметров, у каждой задачи есть следующие параметры.

| Параметр | Описание |
|-------------------| - |
| `Condition` | Необязательный параметр `String`.<br /><br /> Выражение `Boolean`, на основании которого механизм MSBuild определяет, будет ли выполняться эта задача. Сведения о поддерживаемых в MSBuild условиях см. в статье об [условиях](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Необязательный параметр. Может содержать одно из следующих значений:<br /><br /> -   **WarnAndContinue** или **true**. При сбое одной задачи продолжается выполнение сборки и всех последующих задач в элементе [Target](../msbuild/target-element-msbuild.md), а все ошибки из задачи рассматриваются как предупреждения.<br />-   **ErrorAndContinue**. При сбое задачи последующие задачи в элементе `Target` и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как ошибки.<br />-   **ErrorAndStop** или **false** (значение по умолчанию). При сбое задачи отменяется выполнение сборки и последующих задач в элементе `Target`, и фиксируется сбой для выполнения элемента `Target` и всей сборки.<br /><br /> Версии платформы .NET Framework, предшествовавшие 4.5, поддерживали только значения `true` и `false`.<br /><br /> Дополнительные сведения см. в руководстве по [игнорированию ошибок в задачах](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Задача BscMake](../msbuild/bscmake-task.md)|Заключает в оболочку средство "Программа управления сведениями о просмотре Майкрософт" (*bscmake.exe*).|
|[CL - задача](../msbuild/cl-task.md)|Использует оболочку компилятора C++ (*cl.exe*).|
|[Задача CPPClean](../msbuild/cppclean-task.md)|Удаляет временные файлы, которые MSBuild создает при сборке проекта C++.|
|[Задача ClangCompile](../msbuild/clangcompile-task.md)|Использует оболочку компилятора C++ (*clang.exe*).|
|[Задача CustomBuild](../msbuild/custombuild-task.md)|Использует оболочку компилятора C++ (*cmd.exe*).|
|[Задача FXC](../msbuild/fxc-task.md)|Позволяет применять компиляторы шейдеров HLSL в процессе сборки.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Считывает старые журналы отслеживания, записывает новые журналы отслеживания и возвращает набор неактуальных элементов (задача вспомогательного приложения).|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Извлекает имя выходного файла для cl и других средств, которые позволяют указывать только выходной каталог или полное имя файла (задача вспомогательного приложения).|
|[LIB - задача](../msbuild/lib-task.md)|Заключает в оболочку 32-разрядный диспетчер библиотек Майкрософт (*lib.exe*).|
|[Связывание задачи](../msbuild/link-task.md)|Использует оболочку компоновщика C++ (*link.exe*).|
|[MIDL - задача](../msbuild/midl-task.md)|Является оболочкой для компилятора с языка MIDL (*midl.exe*).|
|[MT - задача](../msbuild/mt-task.md)|Является оболочкой для инструмента манифеста Майкрософт (*mt.exe*).|
|[Задача MultiToolTask](../msbuild/multitooltask-task.md)|Нет описания.|
|[Задача ParallelCustomBuild](../msbuild/parallelcustombuild-task.md)|Выполняет параллельные экземпляры [задачи CustomBuild](../msbuild/custombuild-task.md).|
|[RC - задача](../msbuild/rc-task.md)|Является оболочкой для средства компиляции ресурсов Microsoft Windows (*rc.exe*).|
|[Задача SetEnv](../msbuild/setenv-task.md)|Задает или удаляет значение указанной переменной среды.|
|[Базовый класс TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)|Наследует от класса [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[VCMessage - задача](../msbuild/vcmessage-task.md)|Заносит в журнал предупреждения и сообщения об ошибках, возникшие при сборке. (Не расширяется. Только для внутреннего использования.)|
|[Базовый класс VCToolTask](../msbuild/vctooltask-base-class.md)|Наследует от класса [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[XDCMake - задача](../msbuild/xdcmake-task.md)|Является оболочкой для средства XML-документации (*xdcmake.exe*), которая помещает в XML-файл файлы комментариев (*XDC-файлы*) для файла *XML*.|
|[XSD - задача](../msbuild/xsd-task.md)|Создает оболочку для инструмента определения схемы XML (*xsd.exe*), который создает файлы схемы или класса из источника. *См. примечание ниже.*|
|[Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)|Описывает элементы системы MSBuild.|
|[Задачи](../msbuild/msbuild-tasks.md)|Описывает задачи, представляющие собой блоки кода, которые можно объединять для выполнения сборки.|
|[Написание задач](../msbuild/task-writing.md)|Создание задачи.|

> [!NOTE]
> Начиная с версии Visual Studio 2017 поддержка проектов C++ для *xsd.exe* отмечена как нерекомендуемая. Вы можете продолжать использовать API **Microsoft.VisualC.CppCodeProvider**, вручную добавив *CppCodeProvider.dll* в глобальный кэш сборок.
