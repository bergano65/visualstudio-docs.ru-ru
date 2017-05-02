---
title: "Отображение текста на веб-странице (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, запись"
  - "JavaScript, запись текста"
ms.assetid: 3c2455e7-2402-45f2-9545-77a2b2490527
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# Отображение текста на веб-странице (JavaScript)
Существует несколько способов отображения текста на веб\-странице.  Каждый из них имеет свои преимущества и недостатки и предназначен для определенных условий.  
  
## Отображение текста  
  
-   Рекомендуемый способ отображения текста — это создание элемента и запись в его свойство [textContent](http://msdn.microsoft.com/ru-ru/e530667f-f8fa-4b6d-a47c-4d5c75e71265):  
  
    ```javascript  
    <div id="textDiv"></div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        div.textContent = "my text";  
        var text = div.textContent;  
    </script>  
    ```  
  
     В этом примере параметр `text` имеет значение my text.  Однако значение, являющееся результатом получения или задания свойства [textContent](http://msdn.microsoft.com/ru-ru/e530667f-f8fa-4b6d-a47c-4d5c75e71265) в родительском узле, может включать текстовое содержимое из дочерних элементов узла.  В следующем примере показано, что свойство [textContent](http://msdn.microsoft.com/ru-ru/e530667f-f8fa-4b6d-a47c-4d5c75e71265), заданное в дочернем узле, включается в значение свойства [textContent](http://msdn.microsoft.com/ru-ru/e530667f-f8fa-4b6d-a47c-4d5c75e71265) родительского узла:  
  
    ```javascript  
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
  
     В этом примере параметр `text` имеет значение \[nested\].  
  
-   Кроме того, можно создать элемент и выполнить запись в его свойства [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) или [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx).  Значения этих свойств влияют только на текст в самом элементе, но не в его дочерних элементах.  Тем не менее у этих свойств есть и недостатки:  
  
    -   Свойство [InnerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) работает не во всех браузерах, поэтому его часто избегают из соображений совместимости.  
  
    -   Свойство [InnerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) зависит от стилей CSS и не отображается, если элемент является скрытым.  
  
    -   Свойство [InnerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) получает и задает как вложенные узлы, так и текст.  Если оно не защищено, то может быть использовано для атак путем внедрения скрипта.  Кроме того, если в качестве значения этого свойства выбирается текст без HTML\-тегов, все ранее заданные узлы удаляются.  
  
-   Метод `document.write` можно использовать, не создавая элемент,  однако использование этого метода приводит к очистке всей веб\-страницы, что может быть нежелательным.  
  
     В следующем примере показан один из недостатков использования метода `document.write`.  Скрипт должен отображать на экране время каждые 5 секунд, но делает это только два раза.  К моменту второго вызова метода `document.write` страница уже загружена, так что метод `document.write` очищает всю страницу \(вызывает метод `document.open`\).  На этом этапе функция `ShowTime` больше не существует.  
  
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
  
     Чтобы исправить показанный выше код, удалите строку, содержащую метод `document.write`, и комментарии из двух последующих закомментированных строк кода.  
  
-   Можно также использовать функцию `alert`, `prompt` или `confirm`, отображающую сообщение во всплывающем окне.   Обычно использовать всплывающее окно в веб\-браузере не рекомендуется.  Большинство современных браузеров включают параметры, которые автоматически блокируют всплывающие окна, поэтому сообщение может не появиться.  Кроме того, при использовании всплывающих окон можно войти в бесконечный цикл, что не позволит пользователю закрыть веб\-страницу обычным способом.