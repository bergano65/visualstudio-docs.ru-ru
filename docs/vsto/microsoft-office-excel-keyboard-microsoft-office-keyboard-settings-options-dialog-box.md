---
title: "Клавиатура Microsoft Office Excel, настройки клавиатуры Microsoft Office, диалоговое окно &quot;Параметры&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ExcelOptions.KeyboardMappingScheme"
  - "VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard"
  - "VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "сочетания клавиш, разработка решений Office в Visual Studio"
ms.assetid: 2a8b9e70-66fa-4461-8039-b6d8a2fbb963
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Клавиатура Microsoft Office Excel, настройки клавиатуры Microsoft Office, диалоговое окно &quot;Параметры&quot;
  Microsoft Office Excel и Visual Studio могут обрабатывать сочетания клавиш.  Одна и та же комбинация может соответствовать разным командам в Visual Studio и в Excel.  Если приложение Excel открыто в проекте уровня документа в Visual Studio, только одно приложение в заданный момент времени получает команды клавиш быстрого доступа.  По умолчанию на все сочетания откликается Visual Studio, однако, можно изменить настройки таким образом, чтобы приложение Excel откликалось на нажатие сочетания клавиш, если документ имеет фокус. Для этого необходимо выбрать функцию **Динамическая схема клавиатуры**.  
  
 Если в одном из приложений, которое обрабатывает сочетания клавиш, для нажатой комбинации не задана ни одна команда, данная комбинация передается другому приложению.  
  
 Выбранный параметр будет работать для проектов Excel до тех пор, пока пользователь не изменит его.  Выбранные параметры не относятся к проектам Microsoft Office Word; любые изменения для приложения Word необходимо вносить с помощью параметров клавиатуры Microsoft Office Word.  
  
## Список элементов пользовательского интерфейса  
 **Схема клавиатуры Visual Studio**  
 Visual Studio откликается на нажатие сочетания клавиш, даже если приложение Excel имеет фокус.  Например, если нажать функциональную клавишу F5, в то время как приложение Excel имеет фокус, Visual Studio начнет отладку решения.  
  
 **Динамическая схема клавиатуры**  
 Visual Studio откликается на нажатие сочетания клавиш только если оно имеет фокус.  Если приложение Excel имеет фокус, значит приложение Excel будет откликаться на нажатие сочетаний клавиш.  Например, если нажать функциональную клавишу F5 в то время как приложение Excel будет иметь фокус, в Excel откроется диалоговое окно **Переход**.  Если нажать функциональную клавишу F5, в то время как приложение Visual Studio имеет фокус, Visual Studio начнет отладку решения.  
  
## См. также  
 [Клавиатура Microsoft Office Word, настройки клавиатуры Microsoft Office, диалоговое окно "Параметры"](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  