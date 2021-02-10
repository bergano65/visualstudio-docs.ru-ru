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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c8db60044080726b61a02a59cad68d93f683e282
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908823"
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
