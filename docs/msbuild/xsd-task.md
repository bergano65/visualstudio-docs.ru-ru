---
title: Задача XSD | Документы Майкрософт
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (C++))
- MSBuild (C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 217e045a731efa1fe3ba1dda63e89eca685d4b75
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630786"
---
# <a name="xsd-task"></a>XSD - задача

Создает оболочку для инструмента определения схемы XML (*xsd.exe*), который создает файлы схемы или класса из источника.

> [!NOTE]
> Начиная с версии Visual Studio 2017 поддержка проектов C++ для *xsd.exe* отмечена как нерекомендуемая. Вы можете продолжать использовать API **Microsoft.VisualC.CppCodeProvider**, вручную добавив *CppCodeProvider.dll* в глобальный кэш сборок.

## <a name="parameters"></a>Параметры

 В следующей таблице описываются параметры задачи **XSD**.

- **AdditionalOptions**

     Необязательный параметр типа **String**.

     Список параметров, как указано в командной строке. Например, /\<параметр1> /\<параметр2> /\<параметр#>. Этот параметр используется для задания параметров, не представленных другими параметрами задачи **XSD**.

- **GenerateFromSchema**

  Необязательный параметр типа **String**.

  Задает типы, которые создаются из указанной схемы.

  Укажите одно из следующих значений, каждое из которых соответствует параметру XSD.

  - **classes** -  **/classes**

  - **dataset** -  **/dataset**

- **Язык**

     Необязательный параметр типа **String**.

     Задает язык программирования, используемый для созданного кода.

     Доступные варианты: **CS** (C#, по умолчанию), **VB** (Visual Basic) или **JS** (JScript). Также можно указать полное имя класса, реализующего `System.CodeDom.Compiler.CodeDomProvider Class`.

- **Namespace**

     Необязательный параметр типа **String**.

     Определяет пространство имен среды выполнения для создаваемых типов.

- **Sources**

     Обязательный параметр `ITaskItem[]` .

     Определяет массив элементов исходного файла MSBuild, который может использоваться и создаваться задачами.

- **SuppressStartupBanner**

     Необязательный параметр **Boolean** .

     Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.

- **TrackerLogDirectory**

     Необязательный параметр типа **String**.

     Задает каталог для журнала отслеживания.

## <a name="see-also"></a>См. также

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
