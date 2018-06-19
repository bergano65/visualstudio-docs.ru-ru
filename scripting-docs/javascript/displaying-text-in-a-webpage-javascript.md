---
title: Отображение текста на веб-странице (JavaScript) | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, write
- JavaScript, writing text
ms.assetid: 3c2455e7-2402-45f2-9545-77a2b2490527
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8c9ea9d0e0300a0d9b71b0b33d7c99c9ac3935c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569264"
---
# <a name="displaying-text-in-a-webpage-javascript"></a>Отображение текста на веб-странице (JavaScript)
Существует несколько способов отображения текста на веб-странице. Каждый способ имеет свои преимущества и недостатки и предназначен для определенных ситуаций.  
  
## <a name="displaying-text"></a>Отображение текста  
  
-   Для отображения текста рекомендуется создать элемент и сделать запись в свойство textContent этого элемента.  
  
    ```JavaScript  
    <div id="textDiv"></div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        div.textContent = "my text";  
        var text = div.textContent;  
    </script>  
    ```  
  
     В этом примере значение параметра `text` — my text. Однако значение, являющееся результатом получения или задания свойства `textContent` в родительском узле, может включать текстовое содержимое из дочерних элементов узла. В следующем примере показано, что свойство `textContent`, заданное в дочернем узле, включается в значение свойства `textContent` родительского узла.  
  
    ```JavaScript  
    <div id="textDiv">  
        <div id="nested"></div>  
    </div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        var nestedDiv = document.getElementById("nested");  
        nestedDiv.textContent = "nested";  
  
        var text = "[" + div.textContent + "]";  
    </script>  
    ```  
  
     В этом примере значение параметра `text` — [nested].  
  
-   Вы также можете создать элемент и сделать запись в свойства [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) или [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx). Задание этих свойств влияет только на текст в самом элементе, но не в его дочерних элементах. Однако у этих свойств также есть некоторые недостатки.  
  
    -   Свойство [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) работает не во всех браузерах, поэтому для оптимальной совместимости использовать его не рекомендуется.  
  
    -   Свойство [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) зависит от стилей CSS и не отображается, если элемент является скрытым.  
  
    -   С помощью свойства [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) можно получать и задавать вложенные узлы и текст. Если оно не защищено, то может быть использовано для атак путем внедрения скрипта. Кроме того, при задании в качестве его значения текста без HTML-тегов все ранее заданные узлы удаляются.  
  
-   Метод `document.write` можно использовать, не создавая элемент. Однако использование этого метода приводит к очистке всей веб-страницы, что может быть нежелательным.  
  
     В следующем примере показан один из недостатков использования метода `document.write`. Скрипт предназначен для отображения времени каждые 5 секунд, но отображает время только дважды. К моменту второго вызова метода `document.write` загрузка страницы завершена и метод `document.write` очищает всю страницу (вызывает метод `document.open`). На этом этапе функция `ShowTime` больше не существует.  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
    <script type="text/javascript">  
        function ShowTime()  
        {  
            var dt = new Date();  
            document.write(dt.toTimeString());  
            // var elem = document.getElementById("divElem");  
            // elem.textContent = dt.toTimeString();  
            window.setTimeout("ShowTime();", 5000);  
        }  
    </script>  
    </head>  
  
    <body>  
    <script type="text/javascript">  
        ShowTime();  
    </script>  
    <div id="myDiv"></div>  
    </body>  
    </html>  
  
    ```  
  
     Чтобы исправить показанный выше код, удалите строку, содержащую `document.write`, и знаки комментариев из двух последующих закомментированных строк кода.  
  
-   Вы также можете использовать `alert``prompt` или функцию `confirm`, которая отображает сообщение во всплывающем окне. Обычно использовать всплывающее окно в веб-браузере не рекомендуется. В большинстве современных браузеров есть параметры, автоматически блокирующие всплывающие окна, поэтому сообщение может не появиться. Кроме того, при использовании всплывающих окон можно войти в бесконечный цикл, что не позволит пользователю закрыть веб-страницу обычным способом.