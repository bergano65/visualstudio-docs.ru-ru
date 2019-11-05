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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21fdc15b161b7d1cef30effe82e518a174bc9666
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619545"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Создание комментариев XML-документации для JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Комментарии XML-документации* — это комментарии JavaScript, которые добавляются в скрипт для предоставления сведений об элементах кода, таких как функции, поля и переменные. В Visual Studio эти текстовые описания отображаются с IntelliSense при ссылке на функцию скрипта.

 В этом разделе приводится краткое руководство по использованию комментариев XML-документации. Дополнительные сведения об использовании других элементов, таких как [\<var >](../ide/var-javascript.md) и [\<value >](../ide/value-javascript.md), а также дополнительные примеры кода см. в разделе [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md). Сведения о предоставлении информации IntelliSense для асинхронного обратного вызова, например `Promise`, см. в разделе [\<returns >](../ide/returns-javascript.md).

> [!NOTE]
> Комментарии XML-документации доступны только из файлов, сборок и служб со ссылками.

### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Создание комментариев XML-документации для функции JavaScript

- В функции добавьте элементы [\<summary >](../ide/summary-javascript.md), [\<param >](../ide/param-javascript.md)и [\<returns >](../ide/returns-javascript.md) и перед каждым элементом с тремя знаками косой черты (///).

    > [!NOTE]
    > Каждый элемент должен находиться в одной строке.

     В следующем примере показана функция JavaScript.

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

- Чтобы просмотреть комментарии XML-документации, введите имя и открывающую круглую скобку функции, которая помечена комментариями XML-документации, как показано в следующем примере:

    ```javascript
    var areaVal = getArea(
    ```

     При вводе открывающей скобки функции, содержащей комментарии XML-документации, редактор кода использует технологию IntelliSense для вывода сведений, определенных в комментариях к XML-документации.

### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Создание комментариев XML-документации для поля JavaScript

- В определении функции или объекта-конструктора добавьте элемент [\<field >](../ide/field-javascript.md) перед тремя знаками косой черты (///).

     В следующем примере показано использование элемента `<field>` в функции-конструкторе. Дополнительные примеры см. в разделе [\<field >](../ide/field-javascript.md).

    ```javascript
    function Engine() {
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
        this.HorsePower = 150;
    }
    ```

- Чтобы просмотреть комментарии XML-документации, создайте объект с помощью конструктора функции, который помечен комментариями XML-документации, как показано в следующем примере.

    ```javascript
    var eng = new Engine();
    ```

- В следующей строке введите имя объекта и точку, чтобы отобразить сведения IntelliSense для поля.

    ```javascript
    eng.
    ```

### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Создание комментариев XML-документации для перегруженной функции

1. В функции добавьте элемент [> \<signature](../ide/signature-javascript.md) для каждой перегрузки. В этих элементах добавьте другие элементы, такие как `<summary>`, `<param>` и `<returns>`, предшествующие каждому элементу с тремя знаками косой черты (///).

     В следующем примере показана перегруженная функция JavaScript. В этом примере перегрузки отличаются типом параметра.

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

2. Чтобы просмотреть комментарии XML-документации, введите имя и открывающую круглую скобку функции, которая помечена комментариями XML-документации, как показано в следующем примере:

    ```javascript
    calc(
    ```

### <a name="to-create-localized-intellisense"></a>Создание локализованной технологии IntelliSense

1. Создайте XML-файл с комментариями документации в формате Опенажакс Мессажебундле.

    > [!IMPORTANT]
    > Рекомендуемый формат — Мессажебундле. Этот формат не поддерживается в Microsoft AJAX или в WinMD-файлах. Дополнительные сведения об использовании альтернативного формата `VSDoc` см. в разделе [\<loc >](../ide/loc-javascript.md).

     В следующем примере показано содержимое в файле расширения, который содержит локализованные данные IntelliSense. Это XML-файл, расположенный в папке, зависящей от языка и региональных параметров, например JA. Папка должна находиться в том же расположении, что и файл. js, содержащий элемент `<loc>`. Имя файла XML-файла должно соответствовать параметру `filename`, указанному в элементе `<loc>`.

    ```
    <messagebundle>
      <msg name="1">A class that represents a rectangle</msg>
      <msg name="2">The length of the rectangle</msg>
      <msg name="3">The height of the rectangle</msg>
    </messagebundle>

    ```

2. Добавьте в файл. js следующий код. Элемент `<loc>` должен быть объявлен перед любым скриптом и следовать тем же правилам использования, что и элемент `<reference>`. Дополнительные сведения см. в разделе [JavaScript IntelliSense](../ide/javascript-intellisense.md) и [\<loc >](../ide/loc-javascript.md).

    ```javascript
    /// <loc filename="messageFilename.xml" format="messagebundle"/>

    ```

3. В JS-файл добавьте элементы документации XML и описания по умолчанию. Установите `locid` значения атрибутов в соответствии с соответствующими значениями атрибутов `name` из файла расширения. Описания по умолчанию будут заменены локализованными данными IntelliSense, если они доступны.

    ```javascript
    function add(a,b)
    {
        /// <summary locid='1'>description</summary>
        /// <param name='a' locid='2'>parameter a description</param>
        /// <param name='b' locid='3'>parameter b description</param>
    }

    ```

4. Чтобы просмотреть комментарии XML-документации, введите имя и открывающую круглую скобку функции, как показано в следующем примере:

    ```javascript
    add(
    ```

## <a name="see-also"></a>См. также
 [IntelliSense для JavaScript](../ide/javascript-intellisense.md) [Комментарии к XML-документации по](../ide/xml-documentation-comments-javascript.md) [NIB: Пошаговое руководство. JavaScript IntelliSense в ASP.NET](https://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
