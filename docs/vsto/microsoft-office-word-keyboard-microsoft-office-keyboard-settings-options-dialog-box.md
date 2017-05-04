---
title: "Клавиатура Microsoft Office Word, настройки клавиатуры Microsoft Office, диалоговое окно &quot;Параметры&quot; | Microsoft Docs"
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
  - "VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard"
  - "VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard"
  - "VST.WordOptions.KeyboardMappingScheme"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Разработка решений Office в Visual Studio, сочетания клавиш"
ms.assetid: d98edaab-846a-4baa-b190-702b1134754c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Клавиатура Microsoft Office Word, настройки клавиатуры Microsoft Office, диалоговое окно &quot;Параметры&quot;
  Microsoft Office Word и Visual Studio могут обрабатывать сочетания клавиш.  Одна и та же комбинация может соответствовать разным командам в Visual Studio и в Word.  Если приложение Word открыто в проекте уровня документа в Visual Studio, только одно приложение в заданный момент времени получает команды клавиш быстрого доступа.  По умолчанию на все сочетания откликается Visual Studio, однако, можно изменить настройки таким образом, чтобы приложение Word откликалось на нажатие сочетания клавиш, если документ имеет фокус. Для этого необходимо выбрать функцию **Динамическая схема клавиатуры**.  
  
 Если в одном из приложений, которое обрабатывает сочетания клавиш, для нажатой комбинации не задана ни одна команда, данная комбинация передается другому приложению.  
  
 Выбранный параметр будет работать для проектов Word до тех пор, пока пользователь не изменит его.  Выбранные параметры не относятся к проектам Microsoft Office Excel; любые изменения для приложения Excel необходимо вносить с помощью параметров клавиатуры Microsoft Office Excel.  
  
## Список элементов пользовательского интерфейса  
 **Схема клавиатуры Visual Studio**  
 Visual Studio откликается на нажатие сочетания клавиш, даже если документ Word имеет фокус.  Например, если нажать функциональную клавишу F5, в то время как документ имеет фокус, Visual Studio начнет отладку решения.  
  
 **Динамическая схема клавиатуры**  
 Visual Studio откликается на нажатие сочетания клавиш только если оно имеет фокус.  Если документ Word имеет фокус, значит приложение Word будет откликаться на нажатие сочетаний клавиш.  Например, если нажать функциональную клавишу F5 в то время как документ Word будет иметь фокус, в приложении Word откроется диалоговое окно **Найти и заменить** с выбранной вкладкой **Перейти**.  Если нажать функциональную клавишу F5, в то время как приложение Visual Studio имеет фокус, Visual Studio начнет отладку решения.  
  
## См. также  
 [Клавиатура Microsoft Office Excel, настройки клавиатуры Microsoft Office, диалоговое окно "Параметры"](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  