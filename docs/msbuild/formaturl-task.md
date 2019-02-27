---
title: Задача FormatUrl | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6c8bc23a843112a234dad0dfc718937bebfe5aa
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629889"
---
# <a name="formaturl-task"></a>FormatUrl - задача
Преобразовывает URL-адрес в правильный формат URL-адреса.

## <a name="parameters"></a>Параметры
 В следующей таблице приводятся параметры задачи `FormatUrl` .

|Параметр|Описание|
|---------------|-----------------|
|`InputUrl`|Необязательный параметр `String` .<br /><br /> Указывает URL-адрес для форматирования.|
|`OutputUrl`|Необязательный выходной параметр `String`.<br /><br /> Указывает отформатированный URL-адрес.|

## <a name="remarks"></a>Примечания
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)