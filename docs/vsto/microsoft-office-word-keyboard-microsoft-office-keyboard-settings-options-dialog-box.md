---
title: Клавиатура Microsoft Office Word, настройки клавиатуры Microsoft Office, диалоговое окно параметров | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9edd5cd987eb6a4e93b02c8e774adefbc7f969d2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572115"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Word клавиатуре параметры клавиатуры Microsoft Office, параметры-диалоговое окно
  Visual Studio и Microsoft Office Word и обрабатывать сочетания клавиш. Того же сочетания клавиш можно было использовать для различных команд в Word и в Visual Studio. Когда Word открыт в проекте уровня документа в Visual Studio, только одно приложение получает сочетания клавиш. По умолчанию Visual Studio получает сочетания клавиш, но может сделать их получения, если документ имеет фокус, выбрав Word **Динамическая схема клавиатуры**.  
  
 Если используется сочетание клавиш, которое не назначен команде в приложении, которое обрабатывает сочетания клавиш, сочетания клавиш передается другие приложения.  
  
 Выбранного параметра будет работать для проектов Word, пока не потребуется изменить его. Не влияет на выбор проектов Microsoft Office Excel; с помощью Microsoft Office Excel сочетания параметров, необходимо выполнять изменений для Excel.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Схема клавиатуры Visual Studio**  
 Visual Studio получает нажатие сочетания клавиш, даже если документ Word имеет фокус. Например, если нажать клавишу функции **F5** документ имеет фокус, но Visual Studio запускает отладку решения.  
  
 **Динамическая схема клавиатуры**  
 Visual Studio получает сочетания клавиш, только в том случае, когда он получает фокус. Если документ Word имеет фокус, Word получает сочетания клавиш. Например, если нажать клавишу функции **F5** документ Word имеет фокус, будет открыт **поиск и замена** диалоговое окно с **перейти к** с выбранной вкладкой. Если нажать клавишу **F5** Visual Studio имеет фокус, Visual Studio запускает отладку решения.  
  
## <a name="see-also"></a>См. также  
 [Microsoft Office Excel Keyboard, настройки клавиатуры Microsoft Office, параметры-диалоговое окно](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  