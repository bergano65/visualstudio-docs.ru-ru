---
title: Расширение пользовательские настройки и параметры | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user preferences
- user settings [Visual Studio SDK]
- Options dialog box, controlling with the Visual Studio SDK
- VSPackages, user preferences
ms.assetid: 5bb6277a-8c9d-48c8-9b4e-1cb3052caded
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f7b8e1205f98aa701f816f42d7115a5d5ded959
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342811"
---
# <a name="extend-user-settings-and-options"></a>Расширить пользовательские настройки и параметры
В Visual Studio существует два основных способа для сохранения настроек пользователей. **Средства** > **параметры** страницы позволяют пользователям задавать свои собственные значения для различных видов параметры, общие и зависящие от языка. Параметры пользователя позволяют пользователям для задания общих свойств конфигурации Visual Studio. Дополнительные сведения о страницах параметры, см. в разделе [параметры и страницы параметров](../extensibility/internals/options-and-options-pages.md). Дополнительные сведения о пользовательских параметрах см. в разделе [Поддержка пользовательских параметров](../extensibility/internals/support-for-user-settings.md).

- [Создайте страницу параметров](../extensibility/creating-an-options-page.md) описывается создание страницы параметров.

- [Создать категорию параметров](../extensibility/creating-a-settings-category.md) описывается создание категории параметров.

- [Использование хранилища параметров](../extensibility/using-the-settings-store.md) содержит сведения об использовании хранилища параметров.

- [Получение сведений о службе из хранилища параметров](../extensibility/getting-service-information-from-the-settings-store.md) объясняется, как получить доступные службы из хранилища параметров.

- [Записи в хранилище параметров пользователя](../extensibility/writing-to-the-user-settings-store.md) объясняется, как для записи в хранилище параметров пользователя.