---
title: "Доставка расширений Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf74110cf42daa51521cc7ea706c1b951b23deb8
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="shipping-visual-studio-extensions"></a>Доставка расширений Visual Studio
После завершения разработки модуля, можно установить его на других компьютерах, использовать его совместно с друзьями и сотрудниками или опубликовать его в Visual Studio Marketplace. В этом разделе рассматривается, все, что необходимо сделать, чтобы опубликовать и поддерживать расширение: работа с VSIX-файлы, публикации, локализации и обновления.  
  
## <a name="working-with-vsix-extensions"></a>Работа с расширений VSIX  
 Расширения VSIX можно создать путем создания пустой проект VSIX и добавление другой элемент шаблоны. Дополнительные сведения см. в разделе [шаблон проекта VSIX](../extensibility/vsix-project-template.md).  
  
 Формат VSIX в пакет шаблонов проектов, шаблоны, пакеты VSPackage, компоненты Managed Extensibility Framework (MEF), элемент **элементов** элементов управления, сборок и пользовательских типов (включая настраиваемые начальные страницы). Формат VSIX использует развертывание на основе файла. Дополнительные сведения о пакетах VSIX см. в разделе [составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md).  
  
 Формат VSIX не поддерживает установку фрагментов кода. Она также поддерживает некоторых сценариев, таких как запись в глобальный кэш сборок (GAC) или в системный реестр. Если необходимо выполнить запись в глобальном кэше СБОРОК или в реестр с помощью установки, необходимо использовать установщик Windows. Дополнительные сведения см. в разделе [Подготовка расширения для развертывания установщика Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Публикация расширения в Visual Studio Marketplace  
 Расширения другим пользователям можно распространять путем простого рассылка их VSIX-файл, или разместить в на сервере. Лучший способ получить код в руках большое количество пользователей, то чтобы разместить его на [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Расширения Visual Studio Marketplace доступны пользователям Visual Studio с помощью **расширения и обновления**. Дополнительные сведения см. в разделе [поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Полный пример, демонстрирующий отправить расширение для Visual Studio Marketplace см. в разделе [Пошаговое руководство: публикация расширение Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## <a name="private-galleries"></a>Private Galleries  
 При разработке элементов управления, шаблонов и средства, вы можете использовать их в вашей организации путем внесения их в частной коллекции в интрасети. Дополнительные сведения см. в разделе [закрытые галереи](../extensibility/private-galleries.md).  
  
## <a name="localizing-your-extension"></a>Локализация расширения  
 Если планируется выпуска расширения в разных языковых стандартов, следует рассмотреть, локализации. Объяснение этапы см. в разделе [локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="updating-and-versioning-your-extension"></a>Обновление и управление версиями расширения  
 После опубликования расширения придет время, когда необходимо обновить его. Чтобы узнать, как обновить расширения, опубликованную в Visual Studio Marketplace, в разделе [как: обновление расширения](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 Можно установить расширения для поддержки нескольких версий Visual Studio. Дополнительные сведения см. в разделе [поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## <a name="related-topics"></a>Связанные разделы  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Начало работы с шаблоном проекта VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Объясняется, как использовать шаблон проекта VSIX для установки пользовательского шаблона проекта.|  
|[Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Компоненты пакета VSIX.|  
|[Шаблон проекта VSIX](../extensibility/vsix-project-template.md)|Содержит пошаговые инструкции о том, как упаковка и публикация расширения.|  
|[Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)|Описание способов предоставления локализованного текста для процесса установки с помощью файлов extension.vsixlangpack.|  
|[Как: обновление расширения](../extensibility/how-to-update-a-visual-studio-extension.md)|Описывает Обновление расширения в вашей системе и развернуть обновление для существующего расширения Visual Studio.|  
|[Практическое руководство. Добавление зависимости в пакет VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Описывает, как добавить ссылки на пакеты развертывания VSIX.|  
|[Подготовка расширений для развертывания с помощью установщика Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|В этой статье описывается развертывание расширения с помощью установщика Windows.|  
|[Подписывание пакетов VSIX](../extensibility/signing-vsix-packages.md)|Описание для подписания пакетов VSIX.|  
|[Частные коллекции](../extensibility/private-galleries.md)|Описание способов создания закрытые коллекции расширений.|  
|[Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Показано, как ваш модуль поддержки нескольких версий Visual Studio.|
|[Обнаружение Visual Studio](locating-visual-studio.md)|Описывает, как обнаруживать экземпляры Visual Studio для развертывания пользовательского расширения.|
