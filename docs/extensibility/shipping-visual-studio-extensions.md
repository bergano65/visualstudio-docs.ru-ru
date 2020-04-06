---
title: Доставка Визуальные расширения студии (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767bb24bb5cb47f1af1452aa04ebdc91c778e284
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700111"
---
# <a name="shipping-visual-studio-extensions"></a>Доставка расширений Visual Studio
После того как вы закончите разработку расширения, вы можете установить его на других машинах, поделиться им с друзьями и коллегами или опубликовать его на Visual Studio Marketplace. В этом разделе мы объясним все, что вам нужно сделать для того, чтобы опубликовать и сохранить ваше расширение: работа с файлами .vsix, публикация, локализация и обновление.

## <a name="working-with-vsix-extensions"></a>Работа с расширениями VSIX
 Вы можете создать расширения VSIX, создав пустой проект VSIX, а затем добавив в него различные шаблоны элементов. Для получения дополнительной [VSIX Project Template](../extensibility/vsix-project-template.md)информации см.

 Вы можете использовать формат VSIX для упаковки шаблонов проектов, шаблонов элементов, VSPackages, компонентов управляемой расширительности (MEF), элементов управления **Toolbox,** сборок и пользовательских типов (включая пользовательские start Pages for Visual Studio 2017). Формат VSIX использует развертывание на основе файлов. Для получения дополнительной информации о пакетах VSIX [см.](../extensibility/anatomy-of-a-vsix-package.md)

 Формат VSIX не поддерживает установку фрагментов кода. Он также не поддерживает некоторые другие сценарии, такие как письмо в Глобальную ассамблею кэша (GAC) или в системный реестр. Если вам нужно написать в GAC или реестр в установке, вы должны использовать установщик Windows. Для получения дополнительной [информации](../extensibility/preparing-extensions-for-windows-installer-deployment.md)см.

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Публикация расширения на рынок визуальной студии
 Вы можете распространить расширение среди других людей, просто отправив им файл .vsix или поставив на сервер. Но лучший способ получить ваш код в руках многих людей, чтобы положить его на [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Визуальные расширения Studio Marketplace доступны пользователям Visual Studio через **расширения и обновления.** Для получения дополнительной [информации см.](../ide/finding-and-using-visual-studio-extensions.md)

 Для полного примера, который показывает, как загрузить расширение на Visual Studio Marketplace, [см.](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)

## <a name="private-galleries"></a>Private Galleries
 При разработке элементов управления, шаблонов и инструментов вы можете поделиться ими со своей организацией, разместив их в частной галерее в интрасети. Для получения дополнительной информации, см [Частные галереи](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Локализация расширения
 Если вы планируете выпустить расширение в разных местах, следует рассмотреть вопрос о его локализации. Для объяснения того, что в [Localizing VSIX Packages](../extensibility/localizing-vsix-packages.md)этом замешано, см.

## <a name="updating-and-versioning-your-extension"></a>Обновление и обновление расширения
 После того как вы опубликовали расширение, придет время, когда вам нужно обновить его. Чтобы узнать, как обновить расширение, которое было опубликовано на Visual Studio Marketplace, [см.](../extensibility/how-to-update-a-visual-studio-extension.md)

 Вы можете настроить расширение для поддержки нескольких версий Visual Studio. Для получения дополнительной [информации см.](../extensibility/supporting-multiple-versions-of-visual-studio.md)

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Начало работы с шаблоном проекта VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Объясняет, как использовать шаблон проекта VSIX для установки пользовательского шаблона проекта.|
|[Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Описывает компоненты пакета VSIX.|
|[Шаблон проекта VSIX](../extensibility/vsix-project-template.md)|Предоставляет пошаговые инструкции о том, как упаковать и опубликовать расширение.|
|[Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)|Объясняет, как предоставить локализованный текст для процесса установки, используя файлы extension.vsixlangpack.|
|[Практическое руководство: обновление расширения](../extensibility/how-to-update-a-visual-studio-extension.md)|Описывает, как обновить расширение в вашей системе и как развернуть обновление для существующего расширения Visual Studio.|
|[Практическое руководство. Добавление зависимости в пакет VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Описывает, как добавлять ссылки на пакеты развертывания VSIX.|
|[Подготовка расширений для развертывания с помощью установщика Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Объясняет, как развернуть расширение с помощью установки Windows.|
|[Подписывание пакетов VSIX](../extensibility/signing-vsix-packages.md)|Объясняет, как подписать пакеты VSIX.|
|[Частные коллекции](../extensibility/private-galleries.md)|Объясняет, как создавать частные галереи для расширений.|
|[Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Показывает, как поддерживать расширение несколькими версиями Visual Studio.|
|[Обнаружение Visual Studio](locating-visual-studio.md)|Описывает, как найти экземпляры Visual Studio для развертывания пользовательского расширения.|
