---
title: Клавиатура Office Excel, параметры клавиатуры, диалоговое окно "Параметры"
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
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
ms.openlocfilehash: 090e943df2b61352c2342218c3c71c8f0e60eaad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "66836035"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office клавиатура Excel, Microsoft Office параметры клавиатуры, диалоговое окно "Параметры"
  Microsoft Office Excel и Visual Studio работают с сочетаниями клавиш. Одна и та же комбинация клавиш может подключаться для различных команд в Excel и Visual Studio. Когда Excel открыт в проекте уровня документа в Visual Studio, только одно приложение за раз получает команды быстрого вызова. По умолчанию Visual Studio получает все сочетания клавиш, но Excel может получать их, если документ находится в фокусе, выбрав пункт **Динамическая схема клавиатуры**.

 Если вы используете сочетание клавиш, не назначенное команде в приложении, которое в настоящий момент обрабатывает сочетания клавиш, сочетание клавиш передается в другое приложение.

 Выбранный вариант будет действовать для проектов Excel только после его изменения. Выбор не влияет на Microsoft Office проектов Word; необходимо внести любые изменения в Word, используя параметры клавиатуры Microsoft Office Word.

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса
 **Схема клавиатуры Visual Studio** Visual Studio получает все команды сочетания клавиш, даже если в Excel есть фокус. Например, если нажать клавишу **F5** , когда Excel находится в фокусе, Visual Studio начнет отладку решения.

 **Динамическая схема клавиатуры** Visual Studio получает команды сочетаний клавиш только при наличии фокуса. При наличии фокуса Excel получает все команды сочетания клавиш. Например, если нажать клавишу **F5** в то время, как Excel находится в фокусе, Excel откроет диалоговое окно **"перейти** ". Если нажать клавишу **F5** , когда Visual Studio находится в фокусе, Visual Studio начнет отладку решения.

## <a name="see-also"></a>См. также раздел
- [Microsoft Office слово "клавиатура", Microsoft Office параметры клавиатуры, диалоговое окно "Параметры"](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
