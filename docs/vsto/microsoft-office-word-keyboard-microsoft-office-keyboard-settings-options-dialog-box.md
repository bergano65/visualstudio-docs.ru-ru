---
title: Microsoft Office Word Keyboard, настройки клавиатуры Microsoft Office, диалоговое окно "Параметры"
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
ms.openlocfilehash: 6506fec976822ea4a4e675c9961395c952a7a35f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970309"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Word Keyboard, настройки клавиатуры Microsoft Office, диалоговое окно "Параметры"
  Microsoft Office Word и Visual Studio и обрабатывать сочетания клавиш. Же сочетания клавиш могут соответствовать разным командам в Word и в Visual Studio. При открытом в проекте уровня документа в Visual Studio Word только одно приложение за раз получает сочетания клавиш. По умолчанию Visual Studio получает нажатие сочетания клавиш, но может сделать их получения, если документ имеет фокус, выбрав Word **Инамическая схема клавиатуры**.

 При использовании клавиш, которое не назначено команде, в приложении, которое в настоящий момент обрабатывает сочетания клавиш клавиша передается другие приложения.

 Параметр будет работать для проектов Word, пока вы не измените его. Выбор не влияет на проекты Microsoft Office Excel; необходимо выполнять изменений для Excel с помощью Microsoft Office Excel сочетания параметров.

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса
 **Схема клавиатуры Visual Studio** Visual Studio получает нажатие сочетания клавиш, даже если документ имеет фокус. Например, если вы нажмите функциональную клавишу **F5** документ имеет фокус, Visual Studio запускает отладку решения.

 **Динамическая схема клавиатуры** Visual Studio получает сочетания клавиш только в том случае, когда на него установлен фокус. Если документ имеет фокус, Word получает нажатие сочетания клавиш. Например, если вы нажмите функциональную клавишу **F5** документ имеет фокус, открывает Word **поиск и замена** диалоговое окно с **перейти к** выделенной вкладки. Если нажать клавишу **F5** Visual Studio имеет фокус, Visual Studio запускает отладку решения.

## <a name="see-also"></a>См. также
- [Microsoft Office Excel Keyboard, настройки клавиатуры Microsoft Office, диалоговое окно "Параметры"](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
