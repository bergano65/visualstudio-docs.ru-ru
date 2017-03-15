---
title: "Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft. Please include a description of the work you’re doing in Visual Studio and when possible instruction | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_IDWOLEBUSY"
  - "vs.message.0x800A002B"
ms.assetid: 688fdf7e-c3ef-41f1-bc22-9f88f8f5b353
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft. Please include a description of the work you’re doing in Visual Studio and when possible instruction
Серверное приложение занято и не может выполнить текущий запрос.  
  
 Эта ошибка также может быть вызвана антивирусным программным обеспечением, заблокировавшим некоторые процессы devenv.exe.  Для ряда возможностей в продукте используются скрипты, которые могут быть заблокированы антивирусным ПО.  Связанные сведения см. в интерактивном документе "PRB: Visual IDE не открывается при запуске или приложению не удается запустить сообщение об ошибке" на веб\-узле [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;ru\-ru;306905&Product\=vsnet](http://support.microsoft.com/default.aspx?scid=kb;ru-ru;306905&Product=vsnet).  
  
### Исправление ошибок, связанных с серверными приложениями  
  
1.  Выберите команду "Переключиться", чтобы открыть приложение и исследовать проблему.  
  
     —или—  
  
     Нажмите кнопку "Повторить", чтобы подождать, пока серверное приложение закончит обработку запроса.  
  
     —или—  
  
     Нажмите кнопку "Отмена", чтобы прервать обработку запроса.  
  
### Исправление ошибок, связанных с антивирусным ПО  
  
-   В антивирусном программном обеспечении задайте параметр, разрешающий выполнение скриптов, расположенных в devenv.exe.  Подробные инструкции см. в документации к антивирусной программе.