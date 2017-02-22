---
title: "Команда ShowWebBrowser | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "view.showwebbrowser"
helpviewer_keywords: 
  - "ShowWebBrowser - Команда"
  - "View.ShowWebBrowser - команда"
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда ShowWebBrowser
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Отображение URL\-адреса, указанного пользователем в окне браузера, в интегрированной среде разработки \(IDE\) или вне ее.  
  
## Синтаксис  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## Аргументы  
 `URL`  
 Обязательный.  Адрес URL \(Uniform Resource Locator\) веб\-узла.  
  
## Переключатели  
 \/new  
 Необязательный.  Указывает, что страница выводится в новом экземпляре браузера.  
  
 \/ext  
 Необязательный.  Указывает, что страница выводится в браузере по умолчанию вне интегрированной среды разработки \(IDE\).  
  
## Заметки  
 Псевдоним для команды **ShowWebBrowser** – **navigate** или **nav**.  
  
## Пример  
 В следующем примере домашняя страница MSDN Online отображается в браузере вне интегрированной среды разработки \(IDE\).  Если экземпляр браузера открыт, то используется он; в противном случае запускается новый экземпляр браузера.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)