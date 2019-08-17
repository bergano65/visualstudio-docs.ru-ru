---
title: Справочник по неуправляемым API (разработка решений Office в Visual Studio)
ms.date: 08/14/2019
ms.topic: conceptual
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
ms.openlocfilehash: 00db78359154dbda600fb4b58103bc04e89d16b2
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551322"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Справочник по неуправляемым API (разработка решений Office в Visual Studio)

Начиная с версии 2007 Microsoft Office, приложения Office используют интерфейс [интерфейса IManagedAddin](../vsto/imanagedaddin-interface.md) для вызова компонента загрузчика надстроек VSTO, который входит в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]состав. Этот компонент используется для помощи в загрузке управляемых надстроек VSTO. Вы можете создать собственный компонент загрузчика надстроек VSTO, реализовав этот интерфейс.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>Содержание раздела

[Интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md)

COM-интерфейс, который можно реализовать для загрузки и выгрузки управляемых надстроек VSTO в приложениях Office.
