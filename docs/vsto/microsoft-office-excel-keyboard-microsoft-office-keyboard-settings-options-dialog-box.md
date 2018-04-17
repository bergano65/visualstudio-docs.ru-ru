---
title: Клавиатура Microsoft Office Excel, настройки клавиатуры Microsoft Office, диалоговое окно параметров | Документы Microsoft
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
ms.openlocfilehash: 1f052ef4774fe4d5cd4c119eaaf09ed715a2fdbe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Клавиатура Microsoft Office Excel, настройки клавиатуры Microsoft Office, диалоговое окно "Параметры"
  Visual Studio и Microsoft Office Excel и обрабатывать сочетания клавиш. Того же сочетания клавиш можно было использовать для различных команд в Excel и в Visual Studio. Когда Excel открыт в проекте уровня документа в Visual Studio, только одно приложение получает сочетания клавиш. По умолчанию Visual Studio получает сочетания клавиш, но может сделать их получения, если документ имеет фокус, выбрав Excel **Динамическая схема клавиатуры**.  
  
 Если используется сочетание клавиш, которое не назначен команде в приложении, которое обрабатывает сочетания клавиш, сочетания клавиш передается другие приложения.  
  
 Выбранного параметра будет работать для проектов Excel, пока не потребуется изменить его. Не влияет на выбор проектов Microsoft Office Word; необходимо выполнять изменений для Word с помощью Microsoft Office Word сочетания параметров.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Схема клавиатуры Visual Studio**  
 Visual Studio получает нажатие сочетания клавиш, даже если приложение Excel имеет фокус. Например при нажатии клавиши F5 Excel имеет фокус, Visual Studio запускает отладку решения.  
  
 **Динамическая схема клавиатуры**  
 Visual Studio получает сочетания клавиш, только в том случае, когда он получает фокус. Если приложение Excel имеет фокус, Excel получает сочетания клавиш. Например, при нажатии клавиши F5 Excel имеет фокус, откроется приложение Excel **перейти к** диалоговое окно. При нажатии клавиши F5 Visual Studio имеет фокус, Visual Studio запускает отладку решения.  
  
## <a name="see-also"></a>См. также  
 [Клавиатура Microsoft Office Word, настройки клавиатуры Microsoft Office, диалоговое окно "Параметры"](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  