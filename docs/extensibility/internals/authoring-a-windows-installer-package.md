---
title: Создание пакета установщика Windows | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da68fa0a6c115a09ba2050f8c84ea6700ee4fc76
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315790"
---
# <a name="author-a-windows-installer-package"></a>Создать пакет установщика Windows
Диски с данными модели установщика Windows. Вместо того чтобы писать процедурный сценарий для копирования файлов и записи реестра, например, создаваемых строк и столбцов в таблицах базы данных, которые содержат данные файлов и реестра.

## <a name="database-entries"></a>Записи базы данных
Чтобы установить пакет VSPackage, пакет установщика Windows должен содержать записи базы данных для выполнения следующих задач:

- Поиск в системе обнаружения версий [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage поддерживает (с помощью установщика Windows таблицы, в которых AppSearch, CompLocator, RegLocator, DrLocator и подпись).

- Отменить установку, если не поддерживаемая версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установлен или если другой системы пакета VSPackage не требования (с помощью таблицы LaunchCondition).

- Установите пакет VSPackage и зависимые файлы (с помощью каталога, компонентов и таблицы файлов).

- Добавьте соответствующую информацию для VSPackage в реестр (с использованием таблицы реестра).

- Интеграция VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] путем вызова **/Setup для devenv.exe** (с помощью таблицы CustomAction).

Дополнительные сведения см. в разделе [установщика Windows](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Средства установки и настройки
Широкий набор средств установки стороннего предоставляют среду разработки для пакетов установщика Windows. Доступны следующие бесплатные средства:

- InstallShield limited edition

   Ограниченной версии InstallShield можно получить с помощью Visual Studio **новый проект** диалоговое окно. Разверните **другие типы проектов** , а затем выберите **установки и развертывания**. Выберите шаблон, InstallShield.

- Набор инструментов Windows Installer XML

   Набор инструментов Windows Installer XML (WiX) создает пакеты установщика Windows из исходных файлов XML. Набор средств WiX является проектом открытым кодом Майкрософт. Вы можете скачать исходный код и исполняемые файлы из [набора средств Wix](http://sourceforge.net/projects/wix).

   Для коммерческих продуктов, которые интегрируют в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], см. в разделе [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>См. также
- [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)