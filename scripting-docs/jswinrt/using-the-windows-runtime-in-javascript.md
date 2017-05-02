---
title: "Использование среды выполнения Windows в JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Среда выполнения Windows"
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Использование среды выполнения Windows в JavaScript
При создании приложения Магазина Windows Phone или [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] с помощью JavaScript вы можете использовать классы, методы и свойства среды выполнения Windows во многом аналогично тому, как использовали бы собственные объекты, методы и свойства JavaScript.  Данный раздел содержит вводные сведения и ссылки на разделы, где поясняются базовые концепции использования API среды выполнения Windows в JavaScript, включая описание представления типов среды выполнения Windows, использования асинхронных методов среды выполнения Windows, а также ожидания возникновения и обработки событий среды выполнения Windows.  
  
 Справочную документацию JavaScript можно найти в разделе [Справочник по языку JavaScript](../javascript/javascript-language-reference.md).  
  
> [!IMPORTANT]
>  Компоненты среды выполнения Windows недоступны тем приложениям, которые выполняются в Internet Explorer.  
  
## Справочная документация среды выполнения Windows  
 Справочную документацию см. в разделе [Windows Runtime reference](http://msdn.microsoft.com/ru-ru/8fe97dbf-8cd4-435f-b481-9e83d0519f9e).  Примеры кода доступны как на языке JavaScript, так и на языках C\+\+, C\# и Visual Basic.  
  
## Создание компонентов среды выполнения Windows на C\+\+, C\# или Visual Basic  
 Инструкции или указания по написанию компонентов среды выполнения Windows, которые можно использовать в JavaScript, см. в разделе [Создание компонентов среды выполнения Windows](../Topic/Creating%20Windows%20Runtime%20Components.md).  
  
## Соглашения об использовании прописных или строчных букв для компонентов среды выполнения Windows  
 Соглашения об использовании прописных или строчных букв для компонентов среды выполнения Windows в JavaScript немного отличаются от аналогичных соглашений в других языках:  
  
-   Пространства имен и классы указываются в стиле Pascal:  
  
    ```javascript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   Члены классов, включая методы и свойства, и члены структур и перечислений указываются в "верблюжьем" стиле:  
  
    ```javascript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   Имена событий указываются в нижнем регистре:  
  
    ```javascript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## См. также  
 [Вопросы, связанные с использованием API среды выполнения Windows](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [Использование асинхронных методов среды выполнения Windows](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [Обработка событий среды выполнения Windows в JavaScript](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [Представление типов среды выполнения Windows в JavaScript](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Проекция JavaScript для DateTime и TimeSpan среды выполнения Windows](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)