---
title: "Не удалось снабдить файл &quot;&lt;имя_файла&gt;&quot; подписью: &lt;ошибка&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31028"
  - "vbc31028"
helpviewer_keywords: 
  - "BC31028"
ms.assetid: 2cb22e75-5ee2-4e07-afc0-680a0bd543d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удалось снабдить файл &quot;&lt;имя_файла&gt;&quot; подписью: &lt;ошибка&gt;
Произошла ошибка при попытке подписать указанный файл. Эта ошибка могла произойти по следующим причинам:  
  
-   недостаточно разрешений;  
  
-   отсутствуют системные файлы, необходимые для подписывания Authenticode;  
  
-   ссылка указывает на несуществующий сертификат или файл закрытого ключа;  
  
-   неправильно написано имя или URL\-адрес файла.  
  
 **Идентификатор ошибки:** BC31028  
  
### Исправление ошибки  
  
1.  Введите правильные имена сертификата и файла закрытого ключа.  
  
2.  Если вы используете подписывание Authenticode, убедитесь, что файлы Signcode.exe и Javasign.dll существуют, и для них не установлен атрибут "только для чтения".  
  
3.  Убедитесь, что у вас есть разрешение `Write` для файла.  
  
## См. также  
 [File Signing Tool \(Signcode.exe\)](http://msdn.microsoft.com/ru-ru/2d299154-34ea-41ba-ad12-17075bb7e1db)   
 [Deployment and Authenticode Signing](http://msdn.microsoft.com/ru-ru/ecc3f059-da2e-445b-9b87-5b2978e2f8b2)