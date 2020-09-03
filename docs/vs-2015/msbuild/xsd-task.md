---
title: Задача XSD | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0c9dcc0d09887cacca7e6cdaa2e4f2b719c6451c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "67826247"
---
# <a name="xsd-task"></a>Задача XSD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Создает оболочку инструмента определения схемы XML (xsd.exe), который создает файлы схемы или класса из источника.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описываются параметры задачи **XSD**.  
  
- **AdditionalOptions**  
  
     Необязательный **строковый** параметр.  
  
     Список параметров, как указано в командной строке. Например, "*/параметр1/параметр2/параметр№*". Этот параметр используется для задания параметров, не представленных другими параметрами задачи **XSD**.  
  
- **GenerateFromSchema**  
  
  Необязательный **строковый** параметр.  

  Задает типы, которые создаются из указанной схемы.  

  Укажите одно из следующих значений, каждое из которых соответствует параметру XSD.  

  - **классы**  -  **/классес**  

  - **набор данных**  -  **/DataSet**  
  
- **Язык**  
  
     Необязательный **строковый** параметр.  
  
     Задает язык программирования, используемый для созданного кода.  
  
     Доступные варианты: **CS** (C#, по умолчанию), **VB** (Visual Basic) или **JS** (JScript). Также можно указать полное имя класса, реализующего `System.CodeDom.Compiler.CodeDomProvider Class`.  
  
- **Пространство имен**  
  
     Необязательный **строковый** параметр.  
  
     Определяет пространство имен среды выполнения для создаваемых типов.  
  
- **Источники**  
  
     Обязательный параметр `ITaskItem[]` .  
  
     Определяет массив элементов исходного файла MSBuild, который может использоваться и создаваться задачами.  
  
- **SuppressStartupBanner**  
  
     Необязательный **логический** параметр.  
  
     Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.  
  
- **TrackerLogDirectory**  
  
     Необязательный **строковый** параметр.  
  
     Задает каталог для журнала отслеживания.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)
