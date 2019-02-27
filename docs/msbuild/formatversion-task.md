---
title: Задача FormatVersion | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc1651ae769a9dbe8ef8fbd9b8a1a50dd83ea0f6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640718"
---
# <a name="formatversion-task"></a>Задача FormatVersion
Добавляет номер редакции к номеру версии.

-   Случай 1. Вход: Version=\<не определена>; Revision=\<неважно>; выходные данные: OutputVersion="1.0.0.0"

-   Случай 2. Вход: Version="1.0.0.*"  Revision="5"; выходные данные: OutputVersion="1.0.0.5"

-   Случай 3. Вход: Version="1.0.0.0"  Revision=\<неважно>; выходные данные: OutputVersion="1.0.0.0"

## <a name="parameters"></a>Параметры
 В следующей таблице приводятся параметры задачи `FormatVersion` .

|Параметр|Описание|
|---------------|-----------------|
|`FormatType`|Необязательный параметр `String` .<br /><br /> Определяет тип формата.<br /><br /> — "Version" = версия.<br />— "Path" = замените "." на "_".|
|`OutputVersion`|Необязательный выходной параметр `String`.<br /><br /> Указывает выходную версию, содержащую номер редакции.|
|`Revision`|Необязательный параметр `Int32` .<br /><br /> Указывает редакцию, добавляемую к версии.|
|`Version`|Необязательный параметр `String` .<br /><br /> Указывает строку номера версии для форматирования.|

## <a name="remarks"></a>Примечания
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)