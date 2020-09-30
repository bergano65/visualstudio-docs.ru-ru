---
title: Справочник по неуправляемым API (разработка решений Office в Visual Studio)
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
ms.openlocfilehash: 79f48e7771b3e62c0c58fbc59bd9f9b534069d71
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584429"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Справочник по неуправляемым API (разработка решений Office в Visual Studio)

Начиная с версии 2007 Microsoft Office, приложения Office используют интерфейс [интерфейса IManagedAddin](../vsto/imanagedaddin-interface.md) для вызова компонента загрузчика надстроек VSTO, который входит в состав [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Этот компонент используется для помощи в загрузке управляемых надстроек VSTO. Вы можете создать собственный компонент загрузчика надстройки VSTO, реализовав этот интерфейс.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>Содержание раздела

[Интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md)

COM-интерфейс, который можно реализовать для загрузки и выгрузки управляемых надстроек VSTO в приложениях Office.
