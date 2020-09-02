---
title: Клавиатура Office Word, параметры клавиатуры, диалоговое окно "Параметры"
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
ms.openlocfilehash: 5180aa2f4c5022cedcba2c5377d2ff2ac14ffb28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "66835979"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office слово "клавиатура", Microsoft Office параметры клавиатуры, диалоговое окно "Параметры"
  Microsoft Office Word и Visual Studio работают с сочетаниями клавиш. Одна и та же комбинация клавиш может подключаться для различных команд в Word и Visual Studio. Если Word открыт в проекте уровня документа в Visual Studio, то только одно приложение за раз получит команды сочетания клавиш. По умолчанию Visual Studio получает все сочетания клавиш, но вы можете заставить Word получать их, если документ находится в фокусе, выбрав пункт **Динамическая схема клавиатуры**.

 Если вы используете сочетание клавиш, не назначенное команде в приложении, которое в настоящий момент обрабатывает сочетания клавиш, сочетание клавиш передается в другое приложение.

 Выбранный вариант будет действовать для проектов Word только после его изменения. Выбор не влияет на Microsoft Office проекты Excel. необходимо внести любые изменения в Excel, используя параметры клавиатуры Microsoft Office Excel.

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса
 **Схема клавиатуры Visual Studio** Visual Studio получает все сочетания клавиш, даже если документ Word имеет фокус. Например, если нажать клавишу **F5** , когда документ находится в фокусе, Visual Studio начнет отладку решения.

 **Динамическая схема клавиатуры** Visual Studio получает команды сочетаний клавиш только при наличии фокуса. Когда фокус находится в документе Word, Word получает все команды сочетания клавиш. Например, если нажать клавишу **F5** , когда документ Word находится в фокусе, Word открывает диалоговое окно **найти и заменить** с выбранной вкладкой **Перейти к** . Если нажать клавишу **F5** , когда Visual Studio находится в фокусе, Visual Studio начнет отладку решения.

## <a name="see-also"></a>См. также раздел
- [Microsoft Office клавиатура Excel, Microsoft Office параметры клавиатуры, диалоговое окно "Параметры"](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
