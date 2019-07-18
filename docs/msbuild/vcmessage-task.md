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
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d025fd1f71b67acbcd532232b36b55fd35e1f530
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970761"
---
# <a name="vcmessage-task"></a>VCMessage - задача
Заносит в журнал предупреждения и сообщения об ошибках, возникшие при сборке.

## <a name="remarks"></a>Примечания
 Эта задача помогает реализовать MSBuild для Visual C++ и не предназначена для вызова пользователем. Для получения дополнительной информации см. <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Параметры
 В следующей таблице описаны параметры задачи **VCMessage**.

|Параметр|Описание|
|---------------|-----------------|
|**Аргументы**|Необязательный параметр типа **String**.<br /><br /> Разделенный точками с запятой список отображаемых сообщений.|
|**Код**|Обязательный параметр **string**.<br /><br /> Номер ошибки, определяющий сообщение.|
|**Type**|Необязательный параметр типа **String**.<br /><br /> Задает тип выдаваемого сообщения. Укажите "Предупреждение", чтобы выдать предупреждающее сообщение, или "Ошибка", чтобы выдать сообщение об ошибке.|

## <a name="see-also"></a>См. также
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)