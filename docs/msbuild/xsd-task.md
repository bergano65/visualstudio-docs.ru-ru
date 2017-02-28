---
title: "Задача XSD | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9b49f1d51771700c7203f61203575e075c94ae1b
ms.lasthandoff: 02/22/2017

---
# <a name="xsd-task"></a>Задача XSD
Создает оболочку инструмента определения схемы XML (xsd.exe), который создает файлы схемы или класса из источника.  
  
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
  
     Обязательный параметр `ITaskItem[]`.  
  
     Определяет массив элементов исходного файла MSBuild, который может использоваться и создаваться задачами.  
  
-   **SuppressStartupBanner**  
  
     Необязательный параметр типа **Boolean**.  
  
     Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.  
  
-   **TrackerLogDirectory**  
  
     Необязательный параметр типа **String**.  
  
     Задает каталог для журнала отслеживания.  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
