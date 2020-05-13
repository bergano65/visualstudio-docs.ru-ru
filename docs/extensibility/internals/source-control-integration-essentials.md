---
title: Основы интеграции управления исходными словами (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e56658d644720f1563d71d3d08bf35268119112f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705237"
---
# <a name="source-control-integration-essentials"></a>Основные элементы интеграции системы управления версиями
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]поддерживает два типа интеграции управления исходным управлением: плагин управления исходным управлением, который обеспечивает основную функциональность и построен с помощью API подключаемого к Source Control (ранее известного как MSSCCI API), и решение интеграции управления исходным управлением на основе VSPackage, которое обеспечивает более надежную функциональность.

## <a name="source-control-plug-in"></a>Подключаемый модуль управления источником
 Подключаемый модуль управления исходным элементом написан как DLL, который реализует API подключаемых систем управления исходным управлением. Функциональность интеграции регистрации и управления исходным управлением обеспечивается через API. Этот подход проще реализовать, чем управление исходным элементом VSPackage, и он использует пользовательский [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интерфейс (UI) для большинства операций управления исходным управлением.

 Для реализации плагина управления исходным элементом с помощью API-разъема управления исходным управлением выполните следующие действия:

1. Создайте DLL, который реализует функции, указанные в [подключаемых модулих управления исходным управлением.](../../extensibility/source-control-plug-ins.md)

2. Зарегистрируйте DLL, сделав соответствующие записи реестра, как описано в [Как: Установка подключаемого модуля управления источником.](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

3. Создайте утилиту helper и отобразите его по [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запросу пакета адаптера управления исходным управлением (компонент, обрабатывая функциональность управления исходным управлением с помощью плагинов управления исходным управлением).

   Для получения дополнительной информации [см.](../../extensibility/internals/creating-a-source-control-plug-in.md)

## <a name="source-control-vspackage"></a>Управление источником VSPackage
 Реализация VSPackage управления исходным элементом позволяет разработать индивидуальную замену uI управления [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] исходным управлением. Этот подход обеспечивает полный контроль над интеграцией управления исходным управлением, но требует предоставления элементов интерфейса и реализации интерфейсов управления исходным интерфейсом, которые в противном случае были бы предоставлены в соответствии с подходом плагина.

 Для реализации управления исходным элементом VSPackage необходимо:

1. Создайте и зарегистрируйте свой собственный элемент управления исходным ресурсом VSPackage, как описано в [регистрации и отборе.](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

2. Замените пользовательский пользовательский пользовательский элемент управления исходным элементом по умолчанию на пользовательский пользовательский пользовательский элемент. Посмотреть [пользовательский пользовательский интерфейс](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Укажите глифы для использования и обвилите события **глифов Solution Explorer.** Смотрите [Глиф управления](../../extensibility/internals/glyph-control-source-control-vspackage.md).

4. Обработка запроса Edit и событий сохранения запроса, как показано в [запросе Edit Query Сохранить](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).

   Для получения дополнительной информации [см.](../../extensibility/internals/creating-a-source-control-vspackage.md)

## <a name="see-also"></a>См. также
- [Обзор](../../extensibility/internals/source-control-integration-overview.md)
- [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)
