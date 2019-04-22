---
title: Доставка расширений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c7154395be43f6a0b07e9f2557d94fa594ef5ba4
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647205"
---
# <a name="shipping-visual-studio-extensions"></a>Доставка расширений Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Примечание**. В коллекции Visual Studio заменяется в Visual Studio Marketplace. См. в разделе последнюю версию этого раздела за сведениями.

После завершения разработки расширения, можно установить его на других компьютерах, поделиться с друзьями и коллегами или опубликовать его в коллекции Visual Studio. В этом разделе мы расскажем, все, что необходимо сделать, чтобы публикуйте и обслуживайте расширения: работа с VSIX-файлы, публикации, локализация и обновления.

## <a name="working-with-vsix-extensions"></a>Работа с расширений VSIX
 Расширения VSIX можно создать путем создания пустой проект VSIX и добавление шаблонов другого элемента. Дополнительные сведения см. в разделе [шаблоном проекта VSIX](../extensibility/vsix-project-template.md).

 Шаблоны проектов пакетов, элемент шаблоны, пакеты VSPackage, компоненты Managed Extensibility Framework (MEF), можно использовать формат VSIX **элементов** элементов управления, сборок и пользовательских типов (включая настраиваемые начальные страницы). В VSIX используется формат развертывания на основе файлов. Дополнительные сведения о пакетах VSIX см. в разделе [составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 Формат VSIX не поддерживает установку фрагментов кода. Он также поддерживает некоторых других случаях, например запись для глобального кэша сборок (GAC) или в системный реестр. Если необходимо выполнить запись в глобальном кэше СБОРОК или реестра в установку, необходимо использовать установщик Windows. Дополнительные сведения см. в разделе [Подготовка расширения для Windows развертывание с помощью установщика](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-gallery"></a>Публикация расширения в коллекции Visual Studio
 Расширения другим пользователям можно распространять путем простого рассылать их VSIX-файл или помещения в на сервере. Лучший способ получить код в руки со многими людьми, то чтобы поместить его [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Расширения коллекции Visual Studio доступны для пользователей Visual Studio с помощью **расширения и обновления**. Дополнительные сведения см. в разделе [Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Полный пример, в котором показано, как отправить расширение в коллекции Visual Studio, см. в разделе [Пошаговое руководство: Публикация расширения Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Private Galleries
 При разработке элементов управления, шаблоны и средства, вы можете использовать их в вашей организации, публикуя их частную коллекцию в интрасети. Дополнительные сведения см. в разделе [Закрытые коллекции](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Локализация расширения
 Если вы планируете выпуска расширения в разных языков, следует рассмотреть, локализации. Описание показан процесс, см. в разделе [локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Обновление и управление версиями расширения
 После публикации расширения, будут поступать время, когда необходимо обновить его. Чтобы узнать, как обновить расширения, которые были опубликованы в коллекции Visual Studio, см. в разделе [как: Обновление расширения](../extensibility/how-to-update-a-visual-studio-extension.md).

 Можно установить расширения для поддержки нескольких версий Visual Studio. Дополнительные сведения см. в разделе [поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Начало работы с шаблоном проекта VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Объясняется, как использовать шаблон проекта VSIX для установки пользовательского шаблона проекта.|
|[Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Компоненты пакета VSIX.|
|[Шаблон проекта VSIX](../extensibility/vsix-project-template.md)|Содержит пошаговые инструкции о том, как упаковка и публикация расширения.|
|[Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)|Описание способов предоставления локализованного текста для процесса установки с помощью файлов extension.vsixlangpack.|
|[Практическое руководство. Обновление расширения](../extensibility/how-to-update-a-visual-studio-extension.md)|Описывается обновление расширения в системе и развертывание обновления для существующего расширения Visual Studio.|
|[Практическое руководство. Добавление зависимости в пакет VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|В этой статье описывается добавление ссылки на пакет развертывания VSIX.|
|[Подготовка расширений для развертывания с помощью установщика Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|В этой статье описывается развертывание расширения с помощью установщика Windows.|
|[Подписывание пакетов VSIX](../extensibility/signing-vsix-packages.md)|Содержит инструкции по подписи пакетов VSIX.|
|[Частные коллекции](../extensibility/private-galleries.md)|В этой статье описывается создание закрытые коллекции расширений.|
|[Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Показано, как у вашего расширения поддержки нескольких версий Visual Studio.|
