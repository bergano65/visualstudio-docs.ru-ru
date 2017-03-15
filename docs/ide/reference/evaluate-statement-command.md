---
title: "Команда Evaluate Statement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.evaluatestatement"
helpviewer_keywords: 
  - "Debug.EvaluateStatement - команда"
  - "Вычислить оператор - команда"
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Команда Evaluate Statement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Вычисление и отображение заданного оператора.  
  
## Синтаксис  
  
```  
Debug.EvaluateStatement text   
```  
  
## Аргументы  
 `text`  
 Обязательный.  Вычисляемый оператор.  
  
## Заметки  
 Окно для ввода команды **EvaluateStatement** определяет, будет знак равенства \(\=\) рассматриваться как оператор сравнения или оператор присваивания.  
  
 В окне **Команда** знак равенства \(\=\) рассматривается как оператор сравнения.  Так, например, если значения переменных `a` и `b` отличаются, командой  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 будет возвращено значение `false`.  
  
 И наоборот, в окне **Интерпретация** знак равенства \(\=\) рассматривается как оператор присваивания.  Так, например, команда  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 присвоит переменной `a` значение переменной `b`.  
  
## Пример  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## См. также  
 [Команда Print](../../ide/reference/print-command.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)