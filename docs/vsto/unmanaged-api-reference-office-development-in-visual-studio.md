---
title: Справочник по неуправляемым API (разработка решений Office в Visual Studio)
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
ms.openlocfilehash: 4c1616d24ae9b2c072df4e5708eb98e86611a83d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540989"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Справочник по неуправляемым API (разработка решений Office в Visual Studio)

Начиная с версии 2007 Microsoft Office, приложения Office используют интерфейс [интерфейса IManagedAddin](../vsto/imanagedaddin-interface.md) для вызова компонента загрузчика надстроек VSTO, который входит в состав [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Этот компонент используется для помощи в загрузке управляемых надстроек VSTO. Вы можете создать собственный компонент загрузчика надстройки VSTO, реализовав этот интерфейс.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>Содержание раздела

[IManagedAddin - интерфейс](../vsto/imanagedaddin-interface.md)

COM-интерфейс, который можно реализовать для загрузки и выгрузки управляемых надстроек VSTO в приложениях Office.
