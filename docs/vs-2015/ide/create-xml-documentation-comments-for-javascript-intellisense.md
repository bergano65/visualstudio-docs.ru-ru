---
title: Создание комментариев XML-документации для JavaScript IntelliSense | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9fba6ff1b4c56243a47c8b136a25d6f9d593d8e3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701248"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Создание комментариев XML-документации для JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Комментарии XML-документации* являются JavaScript комментарии, добавленные в скрипт для предоставления сведений об элементах кода, например функции, поля и переменные. В Visual Studio эти текстовые описания отображаются с IntelliSense при создании ссылки функции скрипта.  
  
 Здесь представлен базового учебника по использованию комментариев XML-документации. Дополнительные сведения об использовании других элементов, таких как [ \<var >](../ide/var-javascript.md) и [ \<значение >](../ide/value-javascript.md)и Дополнительные примеры кода, см. в разделе [комментарии XML-документации ](../ide/xml-documentation-comments-javascript.md). Сведения о предоставлении сведения IntelliSense для асинхронного обратного вызова, таких как `Promise`, см. в разделе [ \<возвращает >](../ide/returns-javascript.md).  
  
> [!NOTE]
> Комментарии XML-документации доступны только из файлов, сборок и служб со ссылками.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Создание комментариев XML-документации для функции JavaScript  
  
- В функцию, добавьте [ \<summary >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), и [ \<возвращает >](../ide/returns-javascript.md) элементов и перед каждым элементом, с три косой чертой (/ / /).  
  
    > [!NOTE]
    > Каждый элемент должен быть в одной строке.  
  
     В следующем примере функция JavaScript.  
  
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
  
- Для просмотра комментариев XML-документации, введите имя и открывающей скобкой функции, помеченной комментарии XML-документации, как показано в следующем примере:  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     При вводе открывающей скобкой функции, которая содержит комментарии XML-документации, редактор кода используется технологией IntelliSense для отображения информации, которая определена в комментарии XML-документации.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Создавать комментарии XML-документации для JavaScript поля  
  
- В определении функции или объекта конструктора, добавьте [ \<поле >](../ide/field-javascript.md) элемент предшествует три знака косой черты (/ / /).  
  
     В следующем примере показано использование `<field>` элемент в функции конструктора. Дополнительные примеры см. в разделе [ \<поле >](../ide/field-javascript.md).  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
- Чтобы просмотреть комментарии XML-документации, создайте объект, используя конструктор function, помеченный с помощью комментариев XML-документации, как показано в следующем примере.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
- На следующей строке введите имя объекта и точкой для отображения информации IntelliSense для поля.  
  
    ```javascript  
    eng.  
    ```  
  
### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Создание комментариев XML-документации для перегруженной функции  
  
1. В функцию, добавьте [ \<подпись >](../ide/signature-javascript.md) элемент для каждого события перегрузки. В эти элементы, добавить другие элементы, такие как `<summary>`, `<param>`, и `<returns>`, предшествующие каждого элемента с тремя знаками косой черты (/ / /).  
  
     В следующем примере перегруженной функции JavaScript. В этом примере перегрузки отличаются по типу параметра.  
  
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
  
2. Для просмотра комментариев XML-документации, введите имя и открывающей скобкой функции, помеченной комментарии XML-документации, как показано в следующем примере:  
  
    ```javascript  
    calc(  
    ```  
  
### <a name="to-create-localized-intellisense"></a>Чтобы создать локализованную IntelliSense  
  
1. Создайте XML-файл, имеющий комментарии документации в формате MessageBundle альянсе.  
  
    > [!IMPORTANT]
    > MessageBundle — это рекомендуемый формат. Этот формат не поддерживается в Microsoft Ajax, или в файлах winmd. Дополнительные сведения об использовании в качестве альтернативы `VSDoc` форматирования, см. в разделе [ \<loc >](../ide/loc-javascript.md).  
  
     Пример содержимого в файле расширения, который содержит локализованные сведения IntelliSense. Это XML-файл, расположенный в папке для определенного языка и региональных параметров, таких как Япония. Папка должна находиться в том же расположении, что js-файл, который содержит `<loc>` элемент. Имя файла XML-файла должно соответствовать `filename` параметр, указанный в `<loc>` элемент.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2. В файле с расширением JS добавьте следующий код. `<loc>` Элемент должен быть объявлен перед любым скриптом и действуют те же правила использования, как `<reference>` элемент. Дополнительные сведения см. в разделе [IntelliSense для JavaScript](../ide/javascript-intellisense.md) и [ \<loc >](../ide/loc-javascript.md).  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3. В файле с расширением JS добавьте XML-документации элементов и описания по умолчанию. Задайте `locid` значения в соответствии с соответствующих атрибутов `name` значения атрибутов из файла расширения. Описания по умолчанию будет заменен локализованные сведения IntelliSense, если таковой имеется.  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4. Для просмотра комментариев XML-документации, введите имя и открывающей скобкой функции, как показано в следующем примере:  
  
    ```javascript  
    add(  
    ```  
  
## <a name="see-also"></a>См. также  
 [IntelliSense для JavaScript](../ide/javascript-intellisense.md)   
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Пошаговое руководство. IntelliSense для JavaScript в ASP.NET](https://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
