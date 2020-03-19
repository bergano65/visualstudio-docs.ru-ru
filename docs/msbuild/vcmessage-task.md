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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631215"
---
# <a name="vcmessage-task"></a>VCMessage - задача

Заносит в журнал предупреждения и сообщения об ошибках, возникшие при сборке.

## <a name="remarks"></a>Remarks

 Эта задача помогает реализовать MSBuild для проектов C++ и не предназначена для вызова пользователем. Дополнительные сведения см. в разделе <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Параметры

 В следующей таблице описаны параметры задачи **VCMessage**.

|Параметр|Description|
|---------------|-----------------|
|**Аргументы**|Необязательный параметр **String** .<br /><br /> Разделенный точками с запятой список отображаемых сообщений.|
|**Code**|Обязательный параметр **string**.<br /><br /> Номер ошибки, определяющий сообщение.|
|**Тип**|Необязательный параметр **String** .<br /><br /> Задает тип выдаваемого сообщения. Укажите "Предупреждение", чтобы выдать предупреждающее сообщение, или "Ошибка", чтобы выдать сообщение об ошибке.|

## <a name="see-also"></a>См. также раздел

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
