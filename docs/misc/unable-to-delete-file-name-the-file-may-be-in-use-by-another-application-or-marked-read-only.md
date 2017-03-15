---
title: "Unable to delete file &lt;name&gt;. The file may be in use by another application or marked read-only. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_DELETEFILEFAILED"
  - "vs.message.0x800A00A2"
ms.assetid: 5c425dca-1d28-47a8-a11c-6a890be10baf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to delete file &lt;name&gt;. The file may be in use by another application or marked read-only.
Эта ошибка обычно возникает, если удаляемая схема клавиатуры либо используется, либо является схемой только для чтения.  
  
### Чтобы исправить эту ошибку  
  
1.  Если указанный файл используется другим приложением, закройте это приложение.  
  
     —или—  
  
     Если файл является доступен только для чтения, удалите атрибут "только для чтение".  Можно изменить только для чтения, атрибут в диалоговом окне свойства файла, доступного в обозревателе файла.  
  
## См. также  
 [Определение и настройка сочетаний клавиш](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)