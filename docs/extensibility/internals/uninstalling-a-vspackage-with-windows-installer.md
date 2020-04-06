---
title: Установка VSPackage с установкой Windows (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fee88e895d40d42114eaf53422503524594b485f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704278"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Удаление пакета VSPackage с помощью установщика Windows
По большей части, Windows Installer может удалить ваш VSPackage просто "отменить", что он сделал для установки VSPackage. Пользовательские действия, [обсуждаемые в командах, которые должны быть запущены после установки,](../../extensibility/internals/commands-that-must-be-run-after-installation.md) должны быть запущены после удаления. Поскольку вызовы на devenv.exe возникают непосредственно перед стандартным действием InstallFinalize как для установки, так и для неустановки, записи таблиц CustomAction и InstallExecuteSequence обслуживают оба случая.

> [!NOTE]
> Запуск `devenv /setup` после удаления пакета MSI.

 Как правило, если вы добавляете пользовательские действия в пакет Установки Windows, вы должны обрабатывать эти действия во время неустановки и отката. Например, если вы добавляете пользовательские действия для самостоятельной регистрации VSPackage, необходимо также добавить пользовательские действия, чтобы отменить его.

> [!NOTE]
> Пользователь может установить ваш VSPackage, а затем удалить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] версии, с которыми он интегрирован. Вы можете гарантировать, что неустановка VSPackage работает в этом сценарии, устраняя пользовательские действия, которые заходят под код с зависимостями от. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

## <a name="handling-launch-conditions-at-uninstall-time"></a>Обработка условий запуска в неустановленное время
 Стандартное действие LaunchConditions считывает строки таблицы LaunchCondition, чтобы показать сообщения об ошибках, если условия не выполнены. Поскольку условия запуска обычно используются для обеспечения соответствия системным требованиям, обычно `NOT Installed`можно пропустить условия запуска во время неустановки, добавив условие, к ряду LaunchConditions таблицы LaunchCondition.

 Альтернативой является `OR Installed` добавление к условиям запуска, которые не важны при неустановке. Это гарантирует, что условие всегда будет верным во время неустановки и, следовательно, не будет отображать сообщение об ошибке состояния запуска.

> [!NOTE]
> `Installed`является свойством Установки Windows, когда он обнаруживает, что ваш VSPackage уже установлен в системе.

## <a name="see-also"></a>См. также
- [Установщик Windows](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)
