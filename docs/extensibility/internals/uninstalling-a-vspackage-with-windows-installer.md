---
title: Удаление пакета VSPackage с помощью установщика Windows | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ddb09668d3114c055ddac1e4fb677a46754f388
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344765"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Удаление пакета VSPackage с помощью установщика Windows
В большинстве случаев, установщик Windows может удалить VSPackage только по «Отмена», выполненных для установки пакета VSPackage. Пользовательские действия подробно [команды, должен быть запуска после установки](../../extensibility/internals/commands-that-must-be-run-after-installation.md) должна выполняться после удаления также. Так как вызовы devenv.exe выполнялась непосредственно перед стандартное действие функции installfinalize запущенных установок для установки и удаления, записи таблицы CustomAction и InstallExecuteSequence служат в обоих случаях.

> [!NOTE]
> Запустите `devenv /setup` после удаления пакета MSI.

 Как правило при добавлении пользовательских действий в пакет установщика Windows необходимо обрабатывать эти действия во время удаления и отката. Например, при добавлении пользовательских действий для регистрации VSPackage, необходимо добавить настраиваемые действия, чтобы отменить регистрацию, слишком.

> [!NOTE]
> Возможно, пользователь может установить VSPackage и затем удалите версии [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с которой она интегрирована. Вы можете помочь обеспечить работу удаления объекта VSPackage в этом сценарии, устраняя настраиваемых действий, выполнение кода с зависимостями на [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="handling-launch-conditions-at-uninstall-time"></a>Условия запуска обработки во время удаления
 Стандартное действие LaunchConditions считывает строки таблицы LaunchCondition, чтобы показать ошибку сообщения, если условия не выполняются. Так как условия запуска обычно используются для убедитесь, что выполнены требования к системе, обычно можно пропустить условия запуска во время удаления, добавив условие, `NOT Installed`, преобразуется в строку в таблице LaunchCondition LaunchConditions.

 Альтернативным вариантом является добавление `OR Installed` для запуска условия, которые не важны во время удаления. Это гарантирует, что условие всегда будет true во время удаления и таким образом, не будет отображаться сообщение об ошибке условие запуска.

> [!NOTE]
> `Installed` — Это свойство, которое устанавливает установщика Windows, когда обнаруживает, что VSPackage уже был установлен в системе.

## <a name="see-also"></a>См. также
- [Установщик Windows](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)