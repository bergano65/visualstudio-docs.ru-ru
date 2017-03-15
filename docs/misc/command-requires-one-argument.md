---
title: "Command requires one argument. | Microsoft Docs"
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
  - "vs.message.VS_E_INCORRECTPARAMCOUNT1"
  - "vs.message.0x800A00C3"
ms.assetid: b4d98e6d-6970-42fb-b1de-43f2e952fb9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Command requires one argument.
Эта ошибка обычно возникает, если для команды было введено недостаточно данных или если использовалось неверное сочетание аргументов.  
  
 Например, если для команды `alias` было введено `alias` `/delete sample1 sample2`, возникнет данная ошибка, так как псевдоним `/delete` может принимать только одно имя псевдонима, а не два.  Имена псевдонимов не содержат пробелов, поэтому поле **Найти\/Команда** и окно **Команда** интерпретируют `sample1 sample2` как два различных имени псевдонимов.  
  
### Чтобы исправить эту ошибку  
  
1.  Проверьте в документации правильность синтаксиса команды и повторите попытку.  
  
## См. также  
 [Команды Visual Studio](../ide/reference/visual-studio-commands.md)