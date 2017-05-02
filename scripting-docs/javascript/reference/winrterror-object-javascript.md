---
title: "Объект WinRTError (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, WinRTError - объект"
  - "WinRTError - объект [JavaScript]"
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Объект WinRTError (JavaScript)
Если вызов среды выполнения Windows возвращает ошибку HRESULT, указывающую на сбой, JavaScript преобразует ее в специальную ошибку среды выполнения Windows.  Объект доступен только в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], если доступна среда выполнения Windows, в составе глобального пространства имен JavaScript.  
  
## Синтаксис  
  
```  
  
errorObj = new WinRTError();   
```  
  
## Заметки  
 Тип ошибки WinRTError используется только для ошибок, возникающих в API среды выполнения Windows.  
  
## Пример  
 Ниже приведен пример возникновения и перехвата ошибки WinRTError.  
  
```javascript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## Методы  
 У объекта WinRTError нет методов.  
  
## Свойства  
 Объект WinRTError имеет те же свойства, что и объект [Объект Error](../../javascript/reference/error-object-javascript.md).  
  
## Требования  
 Объект WinRTError поддерживается только в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], но не в Internet Explorer.  
  
## См. также  
 [Объект Error](../../javascript/reference/error-object-javascript.md)