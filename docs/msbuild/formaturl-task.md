---
title: Задача FormatUrl | Документы Майкрософт
description: Сведения о том, как с помощью задачи FormatUrl MSBuild преобразовать входной URL-адрес в URL-адрес правильного формата.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e38a0f1aea6999e30d2ab2493873f66cd907878
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436886"
---
# <a name="formaturl-task"></a>FormatUrl - задача

Преобразовывает URL-адрес в правильный формат URL-адреса.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `FormatUrl` .

|Параметр|Описание|
|---------------|-----------------|
|`InputUrl`|Необязательный параметр `String`.<br /><br /> Указывает URL-адрес для форматирования.|
|`OutputUrl`|Необязательный выходной параметр `String`.<br /><br /> Указывает отформатированный URL-адрес.|

## <a name="remarks"></a>Remarks

 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)