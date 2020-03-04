---
title: Задача VCMessage | Документы Майкрософт
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (C++))
- MSBuild (C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2247240ae0992c8275520ec5d7bf94d98ae1053
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631215"
---
# <a name="vcmessage-task"></a>VCMessage - задача

Заносит в журнал предупреждения и сообщения об ошибках, возникшие при сборке.

## <a name="remarks"></a>Примечания

 Эта задача помогает реализовать MSBuild для проектов C++ и не предназначена для вызова пользователем. Для получения дополнительной информации см. <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Параметры

 В следующей таблице описаны параметры задачи **VCMessage**.

|Параметр|Описание|
|---------------|-----------------|
|**Аргументы**|Необязательный параметр типа **String**.<br /><br /> Разделенный точками с запятой список отображаемых сообщений.|
|**Код**|Обязательный параметр **string**.<br /><br /> Номер ошибки, определяющий сообщение.|
|**Type**|Необязательный параметр типа **String**.<br /><br /> Задает тип выдаваемого сообщения. Укажите "Предупреждение", чтобы выдать предупреждающее сообщение, или "Ошибка", чтобы выдать сообщение об ошибке.|

## <a name="see-also"></a>См. также

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
