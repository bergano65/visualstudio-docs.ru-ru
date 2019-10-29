---
title: Создание пакета установщик Windows | Документация Майкрософт
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
ms.openlocfilehash: aa967b5f23ff9f4e5afa67b9b1cb4e83707616c6
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982234"
---
# <a name="author-a-windows-installer-package"></a>Создание пакета установщик Windows
Данные установщик Windows модели. Вместо написания процедурного скрипта для копирования файлов и записи записей реестра, например, создаются строки и столбцы в таблицах базы данных, содержащих данные файлов и реестра.

## <a name="database-entries"></a>Записи базы данных
Чтобы установить VSPackage, пакет установщик Windows должен содержать записи базы данных для выполнения следующих задач:

- Выполните поиск в системе, чтобы найти версии [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддерживаемых VSPackage (с помощью установщик Windows таблиц, включающих Аппсеарч, Комплокатор, Реглокатор, Дрлокатор и Signature).

- Отмените установку, если не установлена поддерживаемая версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] или если не выполнено другое требование к системе VSPackage (с использованием таблицы Лаунчкондитион).

- Установите пакет VSPackage и зависимые файлы (с помощью таблиц каталога, компонента и файлов).

- Добавьте соответствующие сведения для пакета VSPackage в реестр (с помощью таблицы реестра).

- Интегрируйте пакет VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], вызвав **devenv. exe/setup** (с помощью таблицы CustomAction).

Дополнительные сведения см. в разделе [установщик Windows](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Средства установки
Различные средства настройки сторонних разработчиков предоставляют среду разработки для установщик Windows пакетов. Доступны следующие бесплатные средства:

- InstallShield Limited Edition

   Вы можете получить ограниченную версию InstallShield с помощью диалогового окна **Новый проект** Visual Studio. Разверните узел **другие типы проектов** , а затем выберите **Установка и развертывание**. Выберите шаблон InstallShield.

- Набор инструментов установщик Windows XML

   Набор средств установщик Windows XML (WiX) создает установщик Windows пакеты из исходных файлов XML. Набор инструментов WiX — это проект Microsoft с открытым исходным кодом. Исходный код и исполняемые файлы можно загрузить из [набора инструментов WiX](https://sourceforge.net/projects/wix/).

   Сведения о коммерческих продуктах, которые интегрируются в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], см. в разделе [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>См. также
- [Установка пакетов VSPackage с помощью установщик Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)