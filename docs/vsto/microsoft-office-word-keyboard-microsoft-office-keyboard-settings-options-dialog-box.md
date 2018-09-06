---
title: Microsoft Office Word Keyboard, настройки клавиатуры Microsoft Office, диалоговое окно "Параметры"
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
ms.openlocfilehash: 2f0785ec339da51f4f6b52e2093c1bb2ba273285
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673890"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Word Keyboard, настройки клавиатуры Microsoft Office, диалоговое окно "Параметры"
  Microsoft Office Word и Visual Studio и обрабатывать сочетания клавиш. Же сочетания клавиш могут соответствовать разным командам в Word и в Visual Studio. При открытом в проекте уровня документа в Visual Studio Word только одно приложение за раз получает сочетания клавиш. По умолчанию Visual Studio получает нажатие сочетания клавиш, но может сделать их получения, если документ имеет фокус, выбрав Word **Инамическая схема клавиатуры**.  
  
 При использовании клавиш, которое не назначено команде, в приложении, которое в настоящий момент обрабатывает сочетания клавиш клавиша передается другие приложения.  
  
 Параметр будет работать для проектов Word, пока вы не измените его. Выбор не влияет на проекты Microsoft Office Excel; необходимо выполнять изменений для Excel с помощью Microsoft Office Excel сочетания параметров.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Схема клавиатуры Visual Studio**  
 Visual Studio получает нажатие сочетания клавиш, даже если документ имеет фокус. Например, если вы нажмите функциональную клавишу **F5** документ имеет фокус, Visual Studio запускает отладку решения.  
  
 **Динамическая схема клавиатуры**  
 Visual Studio получает сочетания клавиш только в том случае, когда на него установлен фокус. Если документ имеет фокус, Word получает нажатие сочетания клавиш. Например, если вы нажмите функциональную клавишу **F5** документ имеет фокус, открывает Word **поиск и замена** диалоговое окно с **перейти к** выделенной вкладки. Если нажать клавишу **F5** Visual Studio имеет фокус, Visual Studio запускает отладку решения.  
  
## <a name="see-also"></a>См. также  
 [Microsoft Office Excel Keyboard, настройки клавиатуры Microsoft Office, диалоговое окно "Параметры"](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  