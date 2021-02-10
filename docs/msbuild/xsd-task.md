---
title: Задача XSD | Документы Майкрософт
description: Узнайте, как MSBuild использует задачу XSD для создания оболочки для средства xsd.exe определения схемы XML, которое создает файлы схемы или класса из источника.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7227fff5dd4c58e1bce81ef8cad5c32f854abf55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960329"
---
# <a name="xsd-task"></a>XSD - задача

Создает оболочку для инструмента определения схемы XML (*xsd.exe*), который создает файлы схемы или класса из источника.

> [!NOTE]
> Начиная с версии Visual Studio 2017 поддержка проектов C++ для *xsd.exe* отмечена как нерекомендуемая. Вы можете продолжать использовать API **Microsoft.VisualC.CppCodeProvider**, вручную добавив *CppCodeProvider.dll* в глобальный кэш сборок.

## <a name="parameters"></a>Параметры

 В следующей таблице описываются параметры задачи **XSD**.

- **AdditionalOptions**

     Необязательный параметр **String** .

     Список параметров, как указано в командной строке. Например, /\<option1> /\<option2> /\<option#>. Этот параметр используется для задания параметров, не представленных другими параметрами задачи **XSD**.

- **GenerateFromSchema**

  Необязательный параметр **String** .

  Задает типы, которые создаются из указанной схемы.

  Укажите одно из следующих значений, каждое из которых соответствует параметру XSD.

  - **classes** -  **/classes**

  - **dataset** -  **/dataset**

- **Язык**

     Необязательный параметр **String** .

     Задает язык программирования, используемый для созданного кода.

     Доступные варианты: **CS** (C#, по умолчанию), **VB** (Visual Basic) или **JS** (JScript). Также можно указать полное имя класса, реализующего `System.CodeDom.Compiler.CodeDomProvider Class`.

- **Пространство имен**

     Необязательный параметр **String** .

     Определяет пространство имен среды выполнения для создаваемых типов.

- **Источники**

     Обязательный параметр `ITaskItem[]`.

     Определяет массив элементов исходного файла MSBuild, который может использоваться и создаваться задачами.

- **SuppressStartupBanner**

     Необязательный параметр **Boolean** .

     Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.

- **TrackerLogDirectory**

     Необязательный параметр **String** .

     Задает каталог для журнала отслеживания.

## <a name="see-also"></a>См. также раздел

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
