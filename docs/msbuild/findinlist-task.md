---
title: Задача FindInList | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c2f6c5f14f6eff818a265e097f02e2bc76c7372
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996666"
---
# <a name="findinlist-task"></a>FindInList - задача
Выполняет поиск элемента с указанной спецификацией в заданном списке.

## <a name="parameters"></a>Параметры
 В следующей таблице описаны параметры [задачи FindInList](../msbuild/findinlist-task.md).

|Параметр|Описание|
|---------------|-----------------|
|`CaseSensitive`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, при поиске учитывается регистр, в противном случае регистр не учитывается. Значение по умолчанию — `true`.|
|`FindLastMatch`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, возвращается последнее совпадение, в противном случае возвращается первое совпадение. Значение по умолчанию — `false`.|
|`ItemFound`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` , доступный только для чтения.<br /><br /> Первый соответствующий элемент в списке (при его наличии).|
|`ItemSpecToFind`|Обязательный параметр `String` .<br /><br /> Спецификация элементов, которую требуется найти.|
|`List`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Список, в котором нужно найти спецификацию элементов.|
|`MatchFileNameOnly`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, сравнение проводится только по той части спецификации элементов, которая относится к имени файла, в противном случае — по всей спецификации. Значение по умолчанию — `true`.|

## <a name="remarks"></a>Примечания
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)