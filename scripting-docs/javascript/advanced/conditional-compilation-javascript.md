---
title: "Условная компиляция (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ConditionalComp_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "условная компиляция"
  - "условная компиляция, общие сведения"
ms.assetid: a843de4e-3aae-43cd-ad64-477dd00814a2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Условная компиляция (JavaScript)
Условная компиляция позволяет использовать новые языковые функции [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], сохраняя совместимость с предыдущими версиями, не поддерживающими эти функции.  
  
> [!WARNING]
>  Условная компиляция поддерживается во всех версиях Internet Explorer, предшествующих Internet Explorer 11.  В стандартном режиме Internet Explorer 11 и более поздних версий и в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] условная компиляция не поддерживается.  
  
## Операторы  
 Условная компиляция активируется с помощью оператора `@cc_on`, `@if` или `@set`.  Как правило, ее применяют, чтобы использовать новые функции [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], внедрить в скрипт поддержку отладки и отслеживать выполнение кода.  
  
 Всегда помещайте код условной компиляции в комментарии, чтобы основные приложения \(например, Netscape Navigator\), не поддерживающие условную компиляцию, проигнорировали ее.  Пример.  
  
```javascript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
 В данном примере используются специальные разделители комментариев, которые применяются только тогда, когда условная компиляция активируется с помощью оператора `@cc_on`.  Обработчики скриптов, не поддерживающие условную компиляцию, видят только сообщение о том, что условная компиляция не поддерживается.