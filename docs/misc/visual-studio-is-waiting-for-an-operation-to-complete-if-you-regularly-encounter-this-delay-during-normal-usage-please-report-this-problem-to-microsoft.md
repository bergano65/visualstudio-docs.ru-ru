---
title: "Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft. | Microsoft Docs"
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
  - "vs.message.0x800A002A"
  - "vs.message.VB_E_IDWOLENOTRESPONDING"
ms.assetid: 0a4efbb7-72de-43a8-a51a-4a7a24ec743a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft.
Серверное приложение не закончило обработку текущего запроса.  
  
 Эта ошибка также может быть вызвана антивирусным программным обеспечением, заблокировавшим некоторые процессы devenv.exe.  Для ряда возможностей в продукте используются скрипты, которые могут быть заблокированы антивирусным ПО.  Связанные сведения см. в интерактивном документе "PRB: Visual IDE не открывается при запуске или приложению не удается запустить сообщение об ошибке" на веб\-узле [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;ru\-ru;306905&Product\=vsnet](http://support.microsoft.com/default.aspx?scid=kb;ru-ru;306905&Product=vsnet).  
  
### Чтобы исправить эту ошибку  
  
-   Выберите команду "Переключиться", чтобы открыть приложение и исследовать проблему.  
  
     —или—  
  
     Нажмите кнопку "Повторить", чтобы подождать, пока серверное приложение закончит обработку запроса.  
  
### Исправление ошибок, связанных с антивирусным ПО  
  
-   В антивирусном программном обеспечении задайте параметр, разрешающий выполнение скриптов, расположенных в devenv.exe.  Подробные инструкции см. в документации к антивирусной программе.