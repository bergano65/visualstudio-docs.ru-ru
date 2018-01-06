---
title: "Клавиатура Microsoft Office Excel, настройки клавиатуры Microsoft Office, диалоговое окно параметров | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
dev_langs:
- VB
- CSharp
helpviewer_keywords: keyboard shortcuts, Office development in Visual Studio
ms.assetid: 2a8b9e70-66fa-4461-8039-b6d8a2fbb963
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4d082e03ce0edcbbccd6e3dcd8b22ba00a483d91
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
  