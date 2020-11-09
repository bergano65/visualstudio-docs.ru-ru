---
title: Задача VCMessage | Документы Майкрософт
description: Узнайте, как MSBuild использует задачу VCMessage для записи в журнал предупреждений и сообщений об ошибках во время сборки проектов C++.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8c01c86a5374c14ac27de1535020c5deed29a89f
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046746"
---
# <a name="vcmessage-task"></a>VCMessage - задача

Заносит в журнал предупреждения и сообщения об ошибках, возникшие при сборке.

## <a name="remarks"></a>Комментарии

 Эта задача помогает реализовать MSBuild для проектов C++ и не предназначена для вызова пользователем. Для получения дополнительной информации см. <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Параметры

 В следующей таблице описаны параметры задачи **VCMessage**.

|Параметр|Описание|
|---------------|-----------------|
|**Аргументы**|Необязательный параметр **String** .<br /><br /> Разделенный точками с запятой список отображаемых сообщений.|
|**Код**|Обязательный параметр **String**.<br /><br /> Номер ошибки, определяющий сообщение.|
|**Тип**|Необязательный параметр **String** .<br /><br /> Задает тип выдаваемого сообщения. Укажите "Предупреждение", чтобы выдать предупреждающее сообщение, или "Ошибка", чтобы выдать сообщение об ошибке.|

## <a name="see-also"></a>См. также раздел

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
