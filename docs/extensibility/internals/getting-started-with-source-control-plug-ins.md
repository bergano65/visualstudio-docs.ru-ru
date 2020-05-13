---
title: Начало работы с подключаемыми модули управления исходным управлением (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efc21e07830614d9d3041b2d2d231fd82c652114
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708348"
---
# <a name="get-started-with-source-control-plug-ins"></a>Начало работы с плагинами управления исходными источниками
Чтобы создать плагин управления исходным кодом, необходимо создать DLL, который реализует функции, определенные в API [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для подключаемых источников управления, а затем зарегистрировать DLL, чтобы сделать его доступным для использования в управлении исходной версией.

 Для плагинов управления исходным управлением (версии 1.1, 1.2 и 1.3) доступны три версии. API-подключаемый API управления исходным элементом, зарегистрированный здесь, — версия 1.3. Он был разработан, чтобы быть полностью совместимым с плагинами управления исходным управлением, поддерживающими версии 1.1 и 1.2. Что нового в разделе [Подключаемый вариант API 1.3 отдела управления исходным элементом](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) содержит сведения о новых функциях, поддерживаемых в последней версии API подключаемого к источнику управления.

## <a name="in-this-section"></a>В этом разделе
- [Как: Установка плагина управления исходным элементом](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 Описывает, как сделать записи реестра, которые необходимы для подключения управления исходным управлением DLL.

- [Что нового в версии API-элемента управления исходным элементом](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 Предоставляет краткий обзор изменений, внесенных в API-извне управления исходным управлением в версии 1.3.

- [Что нового в версии API-элемента управления исходным элементом](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 Предоставляет краткий обзор изменений, внесенных в API подключаемого элемента управления исходным управлением в версии 1.2.

## <a name="related-sections"></a>См. также
- [Плагины управления исходным элементом](../../extensibility/source-control-plug-ins.md)

 Предоставляет полный список всех элементов в API для управления исходным управлением.

- [Создание плагина управления исходным элементом](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Определяет подключаемый SDK управления исходным элементом и описывает включенные ресурсы.
