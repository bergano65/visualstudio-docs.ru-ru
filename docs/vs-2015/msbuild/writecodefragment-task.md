---
title: Задача WriteCodeFragment | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa9882d30a8483937f77da21bb4700d4899a68a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555482"
---
# <a name="writecodefragment-task"></a>Задача WriteCodeFragment
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Создает временный файл кода из указанного созданного фрагмента кода. Не удаляет этот файл.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `WriteCodeFragment`.  
  
|Параметр|Description|  
|---------------|-----------------|  
|`AssemblyAttributes`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Описание атрибутов для записи. Значение элемента `Include` представляет собой полное имя типа атрибута, например "System.AssemblyVersionAttribute".<br /><br /> Каждый элемент метаданных является парой имя-значение для параметра, который должен иметь тип `String`. Некоторые атрибуты допускают только позиционные аргументы конструктора. Однако подобные аргументы можно использовать в любом атрибуте. Чтобы задать позиционные атрибуты конструктора, используйте имена метаданных, похожие на "_Parameter1", "_Parameter2" и т. д.<br /><br /> Индекс параметра невозможно пропустить.|  
|`Language`|Обязательный параметр `String`.<br /><br /> Задает язык для создаваемого кода.<br /><br /> `Language` может быть любым языком, для которого доступен поставщик CodeDom, например "C#" или "VisualBasic". Выдаваемый файл будет иметь стандартное расширение имени для этого языка.|  
|`OutputDirectory`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает папку назначения для созданного кода, которая обычно является промежуточной.|  
|`OutputFile`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Задает путь к созданному файлу. Если этот параметр задан с помощью имени файла, папка назначения добавляется в начало этого имени. Если он задан с помощью корневой папки, папка назначения игнорируется.<br /><br /> Если этот параметр не задан, имя выходного файла состоит из папки назначения, произвольного имени файла и стандартного расширения для указанного языка.|  
  
## <a name="remarks"></a>Remarks  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описание см. в разделе [базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также:  
 [Операции](../msbuild/msbuild-tasks.md)   
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)
