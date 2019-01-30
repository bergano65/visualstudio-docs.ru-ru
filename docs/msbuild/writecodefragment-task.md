---
title: Задача WriteCodeFragment | Документы Майкрософт
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c99a5c953238498e5a780c2cd731500af2f5c23
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963519"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment - задача
Создает временный файл кода из указанного созданного фрагмента кода. Не удаляет этот файл.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `WriteCodeFragment` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`AssemblyAttributes`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Описание атрибутов для записи. Значение элемента `Include` представляет собой полное имя типа атрибута, например "System.AssemblyVersionAttribute".<br /><br /> Каждый элемент метаданных является парой имя-значение для параметра, который должен иметь тип `String`. Некоторые атрибуты допускают только позиционные аргументы конструктора. Однако подобные аргументы можно использовать в любом атрибуте. Чтобы задать позиционные атрибуты конструктора, используйте имена метаданных, похожие на "_Parameter1", "_Parameter2" и т. д.<br /><br /> Индекс параметра невозможно пропустить.|  
|`Language`|Обязательный параметр `String` .<br /><br /> Задает язык для создаваемого кода.<br /><br /> `Language` может быть любым языком, для которого доступен поставщик CodeDom, например "C#" или "VisualBasic". Выдаваемый файл будет иметь стандартное расширение имени для этого языка.|  
|`OutputDirectory`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает папку назначения для созданного кода, которая обычно является промежуточной.|  
|`OutputFile`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Задает путь к созданному файлу. Если этот параметр задан с помощью имени файла, папка назначения добавляется в начало этого имени. Если он задан с помощью корневой папки, папка назначения игнорируется.<br /><br /> Если этот параметр не задан, имя выходного файла состоит из папки назначения, произвольного имени файла и стандартного расширения для указанного языка.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)