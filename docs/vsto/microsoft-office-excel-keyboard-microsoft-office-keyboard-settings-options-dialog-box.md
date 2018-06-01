---
title: Microsoft Office Excel Keyboard, настройки клавиатуры Microsoft Office, параметры-диалоговое окно
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fc71c699dfea11b8654791efdd52e4c0751a9762
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692451"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Excel Keyboard, настройки клавиатуры Microsoft Office, параметры-диалоговое окно
  Visual Studio и Microsoft Office Excel и обрабатывать сочетания клавиш. Того же сочетания клавиш можно было использовать для различных команд в Excel и в Visual Studio. Когда Excel открыт в проекте уровня документа в Visual Studio, только одно приложение получает сочетания клавиш. По умолчанию Visual Studio получает сочетания клавиш, но может сделать их получения, если документ имеет фокус, выбрав Excel **Динамическая схема клавиатуры**.  
  
 Если используется сочетание клавиш, которое не назначен команде в приложении, которое обрабатывает сочетания клавиш, сочетания клавиш передается другие приложения.  
  
 Выбранного параметра будет работать для проектов Excel, пока не потребуется изменить его. Не влияет на выбор проектов Microsoft Office Word; необходимо выполнять изменений для Word с помощью Microsoft Office Word сочетания параметров.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Схема клавиатуры Visual Studio**  
 Visual Studio получает нажатие сочетания клавиш, даже если приложение Excel имеет фокус. Например, если нажать клавишу функции **F5** Excel имеет фокус, Visual Studio запускает отладку решения.  
  
 **Динамическая схема клавиатуры**  
 Visual Studio получает сочетания клавиш, только в том случае, когда он получает фокус. Если приложение Excel имеет фокус, Excel получает сочетания клавиш. Например, если нажать клавишу функции **F5** Excel имеет фокус, откроется приложение Excel **перейти к** диалоговое окно. Если нажать клавишу **F5** Visual Studio имеет фокус, Visual Studio запускает отладку решения.  
  
## <a name="see-also"></a>См. также  
 [Microsoft Office Word клавиатуре параметры клавиатуры Microsoft Office, параметры-диалоговое окно](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  