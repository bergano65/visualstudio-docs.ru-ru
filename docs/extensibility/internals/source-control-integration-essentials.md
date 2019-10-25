---
title: Основы интеграции системы управления версиями | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcce3d8fdcc1c99c9b91bfebec572033ff3beb1a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723466"
---
# <a name="source-control-integration-essentials"></a>Основные элементы интеграции системы управления версиями
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддерживает два типа интеграции системы управления версиями: подключаемый модуль системы управления версиями, предоставляющий базовые функциональные возможности и построенный с помощью API подключаемого модуля системы управления версиями (ранее известного как API MSSCCI) и решения для интеграции с системой управления версиями на основе VSPackage. Это обеспечивает более надежную функциональность.

## <a name="source-control-plug-in"></a>Подключаемый модуль системы управления версиями
 Подключаемый модуль системы управления версиями записывается в виде библиотеки DLL, реализующей API подключаемого модуля системы управления версиями. Функции интеграции системы регистрации и управления версиями предоставляются через API. Этот подход проще реализовать, чем пакет VSPackage системы управления версиями, и он использует [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательский интерфейс (UI) для большинства операций системы управления версиями.

 Чтобы реализовать подключаемый модуль системы управления версиями с помощью API подключаемого модуля системы управления версиями, выполните следующие действия.

1. Создайте библиотеку DLL, которая реализует функции, указанные в [подключаемых модулях системы управления версиями](../../extensibility/source-control-plug-ins.md).

2. Зарегистрируйте библиотеку DLL, сделав соответствующие записи реестра, как описано в разделе [как установить подключаемый модуль системы управления версиями](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).

3. Создайте вспомогательный пользовательский интерфейс и отобразите его при появлении запроса в пакете адаптера системы управления версиями (компонент [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], который обрабатывает функции управления исходным кодом через подключаемые модули системы управления версиями).

   Дополнительные сведения см. [в разделе Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>Пакет VSPackage системы управления версиями
 Реализация пакета VSPackage системы управления версиями позволяет разрабатывать пользовательские замены для пользовательского интерфейса [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] управления версиями. Такой подход обеспечивает полный контроль над интеграцией системы управления версиями, но требует предоставления элементов пользовательского интерфейса и реализации интерфейсов системы управления версиями, которые в противном случае были бы предоставлены при использовании подключаемого модуля.

 Для реализации пакета VSPackage системы управления версиями необходимо выполнить следующие действия.

1. Создайте и зарегистрируйте собственный пакет VSPackage системы управления версиями, как описано в разделе [Регистрация и выбор](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

2. Замените пользовательский интерфейс системы управления версиями по умолчанию пользовательским ИНТЕРФЕЙСом. См. раздел [настраиваемый пользовательский интерфейс](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Укажите используемые глифы и обрабатывайте **Обозреватель решений** события глифов. См. раздел [элемент управления глифами](../../extensibility/internals/glyph-control-source-control-vspackage.md).

4. Обрабатывает события изменения запроса и сохранения запроса, как показано в запросе [изменить запрос на сохранение](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).

   Дополнительные сведения см. [в разделе Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md).

## <a name="see-also"></a>См. также
- [Обзор](../../extensibility/internals/source-control-integration-overview.md)
- [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)