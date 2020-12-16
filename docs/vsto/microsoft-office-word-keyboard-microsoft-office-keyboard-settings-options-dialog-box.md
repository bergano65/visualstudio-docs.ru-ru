---
title: Клавиатура Office Word, параметры, диалоговое окно "Параметры"
description: Узнайте, как можно заставить Microsoft Word получать сочетания клавиш, если документ имеет фокус, выбрав пункт Динамическая схема клавиатуры.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bf4cfbaf23ad9c1e545af25614722cd52c493df7
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528438"
---
# <a name="microsoft-office-word-keyboard-settings-options-dialog-box"></a>Microsoft Office слово "клавиатура", "Параметры", диалоговое окно "Параметры"
  Microsoft Office Word и Visual Studio работают с сочетаниями клавиш. Одна и та же комбинация клавиш может подключаться для различных команд в Word и Visual Studio. Если Word открыт в проекте уровня документа в Visual Studio, то только одно приложение за раз получит команды сочетания клавиш. По умолчанию Visual Studio получает все сочетания клавиш, но вы можете заставить Word получать их, если документ находится в фокусе, выбрав пункт **Динамическая схема клавиатуры**.

 Если вы используете сочетание клавиш, не назначенное команде в приложении, которое в настоящий момент обрабатывает сочетания клавиш, сочетание клавиш передается в другое приложение.

 Выбранный вариант будет действовать для проектов Word только после его изменения. Выбор не влияет на Microsoft Office проекты Excel. необходимо внести любые изменения в Excel, используя параметры клавиатуры Microsoft Office Excel.

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса
 **Схема клавиатуры Visual Studio** Visual Studio получает все сочетания клавиш, даже если документ Word имеет фокус. Например, если нажать клавишу **F5** , когда документ находится в фокусе, Visual Studio начнет отладку решения.

 **Динамическая схема клавиатуры** Visual Studio получает команды сочетаний клавиш только при наличии фокуса. Когда фокус находится в документе Word, Word получает все команды сочетания клавиш. Например, если нажать клавишу **F5** , когда документ Word находится в фокусе, Word открывает диалоговое окно **найти и заменить** с выбранной вкладкой **Перейти к** . Если нажать клавишу **F5** , когда Visual Studio находится в фокусе, Visual Studio начнет отладку решения.

## <a name="see-also"></a>См. также раздел
- [Microsoft Office клавиатура Excel, Microsoft Office параметры клавиатуры, диалоговое окно "Параметры"](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
