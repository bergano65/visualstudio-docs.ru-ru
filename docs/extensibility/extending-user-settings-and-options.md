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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00ccae86029e43933d5624c955ed6bfcc0a045be
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697275"
---
# <a name="extend-user-settings-and-options"></a>Расширить пользовательские настройки и параметры
В Visual Studio существует два основных способа для сохранения настроек пользователей. **Средства** > **параметры** страницы позволяют пользователям задавать свои собственные значения для различных видов параметры, общие и зависящие от языка. Параметры пользователя позволяют пользователям для задания общих свойств конфигурации Visual Studio. Дополнительные сведения о страницах параметры, см. в разделе [параметры и страницы параметров](../extensibility/internals/options-and-options-pages.md). Дополнительные сведения о пользовательских параметрах см. в разделе [Поддержка пользовательских параметров](../extensibility/internals/support-for-user-settings.md).

- [Создайте страницу параметров](../extensibility/creating-an-options-page.md) описывается создание страницы параметров.

- [Создать категорию параметров](../extensibility/creating-a-settings-category.md) описывается создание категории параметров.

- [Использование хранилища параметров](../extensibility/using-the-settings-store.md) содержит сведения об использовании хранилища параметров.

- [Получение сведений о службе из хранилища параметров](../extensibility/getting-service-information-from-the-settings-store.md) объясняется, как получить доступные службы из хранилища параметров.

- [Записи в хранилище параметров пользователя](../extensibility/writing-to-the-user-settings-store.md) объясняется, как для записи в хранилище параметров пользователя.