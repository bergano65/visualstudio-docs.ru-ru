---
title: "Параметр devenv.exe InstallVSTemplates | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /InstallVSTemplates switch
- /InstallVSTemplates Devenv switch
- InstallVSTemplates switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 529979caa801ace8dd649cf1614f2eeb27ca070b
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2018
---
# <a name="installvstemplates-devenvexe"></a>/InstallVSTemplates (devenv.exe)

Параметр /InstallVSTemplates регистрирует шаблоны проектов или элементов, которые находятся в папке *\<путь_установки_Visual_Studio>*\Common7\IDE\ProjectTemplates\ или *\<путь_установки_Visual_Studio>*\Common7\IDE\ItemTemplates\, чтобы они были доступны в диалоговых окнах **Создание проекта** и **Добавление нового элемента**.

> [!WARNING]
> Этот параметр поддерживается только при партнерской разработке Visual Studio. Для использования параметров [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) и [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) нужно запустить devenv от имени администратора. Дополнительные сведения см. в разделе [Разрешения пользователей](../../ide/user-permissions-and-visual-studio.md).

## <a name="syntax"></a>Синтаксис

```
devenv.exe /InstallVSTemplates
```

## <a name="see-also"></a>См. также

[Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)