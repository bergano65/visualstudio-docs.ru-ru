---
title: "Практическое руководство. Создание комментариев XML-документации для JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "комментарии к коду, IntelliSense для JavaScript"
  - "комментарии документации [JavaScript]"
  - "IntelliSense [JavaScript], комментарии XML-документации"
  - "комментарии XML-документации, IntelliSense для JavaScript"
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Практическое руководство. Создание комментариев XML-документации для JavaScript
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Комментарии XML\-документации* , JavaScript комментарии добавить сценарий для предоставления сведений об элементах кода, такие как функции, поля и переменные.  В Visual Studio эти текстовые описания отображаются с IntelliSense, при ссылке на функцию сценария.  
  
 Этот раздел предоставляет основные учебник по с помощью комментариев XML\-документации.  Дополнительные сведения об использовании других элементов, таких как [\<var\>](../ide/var-javascript.md) и [\<value\>](../ide/value-javascript.md)и Дополнительные примеры кода, см. [Комментарии XML\-документации](../ide/xml-documentation-comments-javascript.md).  Сведения о предоставлении информации IntelliSense для асинхронного обратного вызова, таких как `Promise`, см. [\<returns\>](../ide/returns-javascript.md).  
  
> [!NOTE]
>  Комментарии XML\-документации, доступны только из файлов, сборок и служб.  
  
### Чтобы создать функцию JavaScript для комментариев XML\-документации  
  
-   Добавьте в функцию [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md), и [\<returns\>](../ide/returns-javascript.md) элементы и предшествовать каждый элемент с тремя знаками косой черты \(\/ \/ \/\).  
  
    > [!NOTE]
    >  Каждый элемент должен быть в одной строке.  
  
     Пример функции JavaScript.  
  
    ```javascript  
    function getArea(radius)  
    {  
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>  
        /// <param name="radius" type="Number">The radius of the circle.</param>  
        /// <returns type="Number">The area.</returns>  
        var areaVal;  
        areaVal = Math.PI * radius * radius;  
        return areaVal;  
    }  
    ```  
  
-   Чтобы просмотреть комментарии XML\-документации, введите имя и открывающую скобку функции, помеченные комментарии XML\-документации, как показано в следующем примере:  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     При вводе открывающей скобки функции, которая содержит комментарии XML\-документации в редакторе кода используется IntelliSense для отображения сведений, определенных в комментарии XML\-документации.  
  
### Создавать комментарии XML\-документации для поля JavaScript  
  
-   Добавьте в конструктор объекта или функции определения [\<field\>](../ide/field-javascript.md) элемент предшествует три косой черты \(\/ \/ \/\).  
  
     В следующем примере показано использование `<field>` элемент в функции конструктора.  Дополнительные примеры см. в разделе [\<field\>](../ide/field-javascript.md).  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   Чтобы просмотреть комментарии XML\-документации, следует создайте объект с помощью функции конструктора, помеченного с комментариями документации XML, как показано в следующем примере.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   В следующей строке введите имя объекта и отображать сведения о IntelliSense в поле период.  
  
    ```javascript  
    eng.  
    ```  
  
### Создавать комментарии XML\-документации для перегруженной функции  
  
1.  Добавьте в функцию [\<signature\>](../ide/signature-javascript.md) элемента для каждой перегрузки.  В этих элементах добавлять другие элементы, такие как `<summary>`, `<param>`, и `<returns>`, предшествующего каждый элемент с тремя косой черты \(\/ \/ \/\).  
  
     В следующем примере показано перегруженной функции JavaScript.  В этом примере перегрузки отличаются по типу параметра.  
  
    ```javascript  
    function calc(a) {  
        /// <signature>  
        /// <summary>Function summary 1.</summary>  
        /// <param name="a" type="Number">A number.</param>  
        /// <returns type="Number" />  
        /// </signature>  
        /// <signature>  
        /// <summary>Function summary 2.</summary>  
        /// <param name="a" type="String">A string.</param>  
        /// <returns type="Number" />  
        /// </signature>  
        return a;  
    }  
    ```  
  
2.  Чтобы просмотреть комментарии XML\-документации, введите имя и открывающую скобку функции, помеченные комментарии XML\-документации, как показано в следующем примере:  
  
    ```javascript  
    calc(  
    ```  
  
### Для создания локализованных IntelliSense  
  
1.  Создайте XML\-файл, содержащий комментарии документации в формате MessageBundle альянсе.  
  
    > [!IMPORTANT]
    >  MessageBundle — это рекомендуемый формат.  Этот формат не поддерживается в Microsoft Ajax или в файлах .winmd.  Дополнительные сведения об использовании вместо `VSDoc` формат, см. [\<loc\>](../ide/loc-javascript.md).  
  
     В следующем примере показано содержимое в сопроводительным файлом, содержащий локализованные сведения IntelliSense.  Это XML\-файл, который находится в папке определенного языка и региональных параметров, например JA.  Папка должна находиться в той же папке, как JS\-файла, который содержит `<loc>` элемент.  Имя файла XML\-файл должен соответствовать `filename` параметр, указанный в `<loc>` элемент.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  В JS\-файла добавьте следующий код.  `<loc>` Элемент должен быть объявлен перед любым сценарием и следует тем же правилам использования как `<reference>` элемент.  Дополнительные сведения см. в разделах [IntelliSense для JavaScript](../ide/javascript-intellisense.md) и [\<loc\>](../ide/loc-javascript.md).  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  В JS\-файла добавьте XML\-документации элементов и описания по умолчанию.  Установка `locid` значения в соответствии с соответствующих атрибутов `name` значения атрибутов с сопроводительным файлом.  Описание по умолчанию будут заменены локализованные сведения IntelliSense, если он доступен.  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4.  Чтобы просмотреть комментарии XML\-документации, введите имя и открывающую скобку функции, как показано в следующем примере:  
  
    ```javascript  
    add(  
    ```  
  
## См. также  
 [IntelliSense для JavaScript](../ide/javascript-intellisense.md)   
 [Комментарии XML\-документации](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Walkthrough: JavaScript IntelliSense in ASP.NET](http://msdn.microsoft.com/ru-ru/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
