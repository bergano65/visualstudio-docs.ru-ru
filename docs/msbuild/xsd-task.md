---
title: Задача XSD | Документы Майкрософт
ms.custom: ''
ms.date: 06/27/2018
ms.technology: msbuild
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
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b292c0bf1bc80f811cbf2f845385f91987184674
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057376"
---
# <a name="xsd-task"></a>Задача XSD
Создает оболочку инструмента определения схемы XML (xsd.exe), который создает файлы схемы или класса из источника.  

> [!NOTE]
> В Visual Studio 2017 поддержка проектов C++ для xsd.exe признана нерекомендуемой. Вы можете продолжать использовать API **Microsoft.VisualC.CppCodeProvider**, вручную добавив **CppCodeProvider.dll** в глобальный кэш сборок. 
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описываются параметры задачи **XSD**.  
  
-   **AdditionalOptions**  
  
     Необязательный параметр типа **String**.  
  
     Список параметров, как указано в командной строке. Например, "*/параметр1 /параметр2 /параметр#*". Этот параметр используется для задания параметров, не представленных другими параметрами задачи **XSD**.  
  
-   **GenerateFromSchema**  
  
     Необязательный параметр типа **String**.  
  
     Задает типы, которые создаются из указанной схемы.  
  
     Укажите одно из следующих значений, каждое из которых соответствует параметру XSD.  
  
    -   **classes** - **/classes**  
  
    -   **dataset** - **/dataset**  
  
-   **Язык**  
  
     Необязательный параметр типа **String**.  
  
     Задает язык программирования, используемый для созданного кода.  
  
     Доступные варианты: **CS** (C#, по умолчанию), **VB** (Visual Basic) или **JS** (JScript). Также можно указать полное имя класса, реализующего `System.CodeDom.Compiler.CodeDomProvider Class`.  
  
-   **Namespace**  
  
     Необязательный параметр типа **String**.  
  
     Определяет пространство имен среды выполнения для создаваемых типов.  
  
-   **Sources**  
  
     Обязательный параметр `ITaskItem[]` .  
  
     Определяет массив элементов исходного файла MSBuild, который может использоваться и создаваться задачами.  
  
-   **SuppressStartupBanner**  
  
     Необязательный параметр типа **Boolean**.  
  
     Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.  
  
-   **TrackerLogDirectory**  
  
     Необязательный параметр типа **String**.  
  
     Задает каталог для журнала отслеживания.  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)