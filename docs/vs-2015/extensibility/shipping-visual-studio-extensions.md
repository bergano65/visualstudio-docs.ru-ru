---
title: Модули доставки | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150794"
---
# <a name="shipping-visual-studio-extensions"></a>Доставка расширений Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Примечание**. коллекция Visual Studio заменяется Visual Studio Marketplace. Дополнительные сведения см. в последней версии этого раздела.

После завершения разработки расширения вы можете установить его на других компьютерах, поделиться им с вашими друзьями и сотрудниками или опубликовать его в галерее Visual Studio. В этом разделе описываются все вещи, необходимые для публикации и обслуживания расширения: работа с файлами VSIX, публикация, локализация и обновление.

## <a name="working-with-vsix-extensions"></a>Работа с расширениями VSIX
 Расширения VSIX можно создать, создав пустой проект VSIX, а затем добавив в него различные шаблоны элементов. Дополнительные сведения см. в разделе [шаблон проекта VSIX](../extensibility/vsix-project-template.md).

 Формат VSIX можно использовать для упаковки шаблонов проектов, шаблонов элементов, пакетов VSPackage, Managed Extensibility Framework (MEF), элементов управления **панели элементов** , сборок и пользовательских типов (включая пользовательские начальные страницы). Формат VSIX использует развертывание на основе файлов. Дополнительные сведения о пакетах VSIX см. [в разделе Анатомия пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 Формат VSIX не поддерживает установку фрагментов кода. Он также не поддерживает некоторые другие сценарии, такие как запись в глобальный кэш сборок (GAC) или в системный реестр. Если необходимо выполнить запись в глобальный кэш сборок или в реестр в установке, необходимо использовать установщик Windows. Дополнительные сведения см. в разделе [Подготовка расширений для установщик Windows развертывания](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-gallery"></a>Публикация расширения в коллекции Visual Studio
 Вы можете распространить расширение другим людям, просто передавая им VSIX-файл или поместив его на сервер. Но лучший способ получить код в практических занятиях — поместить его в [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Расширения коллекции Visual Studio доступны для пользователей Visual Studio с помощью **расширений и обновлений**. Дополнительные сведения см. в разделе [Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Полный пример, демонстрирующий передачу расширения в коллекцию Visual Studio, см. в разделе [Пошаговое руководство. публикация расширения Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Private Galleries
 При разработке элементов управления, шаблонов и средств вы можете поделиться ими с Организацией, разместив их в частную галерею в интрасети. Дополнительные сведения см. в разделе [частные галереи](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Локализация расширения
 Если вы планируете выпустить расширение в разных языковых стандартах, рекомендуется локализовать его. Объяснение того, что участвует в этой статье, см. в разделе [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Обновление и управление версиями вашего расширения
 После публикации расширения появится время, когда необходимо обновить его. Сведения о том, как обновить расширение, опубликованное в коллекции Visual Studio, см. в разделе [руководство. обновление расширения](../extensibility/how-to-update-a-visual-studio-extension.md).

 Вы можете настроить расширение для поддержки нескольких версий Visual Studio. Дополнительные сведения см. в разделе [Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Начало работы с шаблоном проекта VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Объясняется, как использовать шаблон проекта VSIX для установки пользовательского шаблона проекта.|
|[Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Описывает компоненты пакета VSIX.|
|[Шаблон проекта VSIX](../extensibility/vsix-project-template.md)|Содержит пошаговые инструкции по упаковке и публикации расширения.|
|[Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)|Объясняет, как предоставить локализованный текст для процесса установки с помощью файлов extension. всикслангпакк.|
|[Практическое руководство: обновление расширения](../extensibility/how-to-update-a-visual-studio-extension.md)|Описывает, как обновить расширение в системе и как развернуть обновление для существующего расширения Visual Studio.|
|[Практическое руководство. Добавление зависимости в пакет VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Описывает добавление ссылок в пакеты развертывания VSIX.|
|[Подготовка расширений для развертывания с помощью установщика Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|В этой статье объясняется, как развернуть расширение с помощью установщик Windows.|
|[Подписывание пакетов VSIX](../extensibility/signing-vsix-packages.md)|Описывает, как подписывать пакеты VSIX.|
|[Частные коллекции](../extensibility/private-galleries.md)|Описание создания частных коллекций для расширений.|
|[Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Показывает, как расширение поддерживает несколько версий Visual Studio.|
