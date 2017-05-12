---
title: "this не может быть присвоено значение | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5000"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# this не может быть присвоено значение
Предпринята попытка присвоить значение объекту **this**.  **this** — это ключевое слово [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], которое ссылается на:  
  
-   объект, который в данный момент выполняет метод;  
  
-   глобальный объект, если текущий метод отсутствует \(или метод не принадлежит любому другому объекту\).  
  
 Методом называется функция [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], вызываемая с помощью объекта.  Внутри метода ключевое слово **this** является ссылкой на объект, с помощью которого вызывается метод \(этот объект часто создается посредством вызова конструктора класса с помощью оператора **new**\).  
  
 Ключевое слово **this** можно использовать в методе для ссылки на текущей объект, но **this** нельзя присвоить новое значение.  
  
### Исправление ошибки  
  
-   Не пытайтесь присвоить значение ключевому слову **this**.  Чтобы получить доступ к свойству или методу экземпляра объекта, используйте оператор "точки" \(например, circle**.**radius\).  
  
    > [!NOTE]
    >  Не допускается присваивать пользовательской переменной имя **this**, поскольку оно является зарезервированным словом языка [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## См. также  
 [Оператор this](../../javascript/reference/this-statement-javascript.md)   
 [Устранение неполадок скриптов](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)