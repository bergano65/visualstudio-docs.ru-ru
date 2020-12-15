---
title: Справочник по неуправляемым API (разработка решений Office в Visual Studio)
description: Ссылка на неуправляемый API используется для загрузки надстроек VSTO, управляемых с помощью. Вы также можете создать собственный компонент загрузчика надстройки VSTO, реализовав этот интерфейс.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9dbb64b54d9b0dd9a244d9a614fbce211d1edfc5
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522691"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Справочник по неуправляемым API (разработка решений Office в Visual Studio)

Начиная с версии 2007 Microsoft Office, приложения Office используют интерфейс [интерфейса IManagedAddin](../vsto/imanagedaddin-interface.md) для вызова компонента загрузчика надстроек VSTO, который входит в состав [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Этот компонент используется для помощи в загрузке управляемых надстроек VSTO. Вы можете создать собственный компонент загрузчика надстройки VSTO, реализовав этот интерфейс.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>В этом разделе

[Интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md)

COM-интерфейс, который можно реализовать для загрузки и выгрузки управляемых надстроек VSTO в приложениях Office.
