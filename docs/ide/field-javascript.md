---
title: "&lt;field&gt; (JavaScript) | Microsoft Docs"
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
  - "XML-тег JavaScript <field>"
  - "field - XML-тег JavaScript"
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;field&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Указывает данные по документации, включая описание, или для поля или члена, определенные для объекта.  
  
## Синтаксис  
  
```  
<field name="fieldName" static="true|false"  
    type="FieldType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID"  
    value="code">description  
</field>  
```  
  
#### Параметры  
 `name`  
 Имя поля или элемента.  Если элемент `<field>` используется в конструктор, не требуется и определяет элемент `name`, к которому применяется тег.  Если элемент `<field>` напрямую аннотирует поле, этот атрибут игнорируется и используемое имя Visual Studio имя реального поля в исходном коде.  
  
 `static`  
 Необязательный.  Определяет, является ли поле член функции конструктора или член объекта, возвращенного функцией конструктора.  Установить значение `true` для отображения поля в качестве члена функции конструктора.  Установить значение `false` для отображения поля в качестве члена объекта является функцией конструктора.  
  
 `type`  
 Необязательный.  Тип данных поля.  Тип может быть одним из следующих:  
  
-   Тип языка ECMAScript в спецификации ECMAScript 5, такие как `Number` и `Object`.  
  
-   Объект DOM, например `HTMLElement`, `Window` и `Document`.  
  
-   Функция конструктора JavaScript.  
  
 `integer`  
 Необязательный.  Если свойство `type` имеет значение `Number`, указывает ли поле целое число.  Установите значение `true`, чтобы указать, что поле целое число; в противном случае укажите значение `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `domElement`  
 Необязательный.  Этот атрибут выступан против; атрибут `type` имеет приоритет над этим атрибутом.  Этот атрибут задает ли документированное поле элемента DOM.  Задайте значение `true` для указания того, что поле элемента DOM; в противном случае укажите значение `false`.  Если атрибут `type` не задан, а параметр `domElement` имеет значение `true`, то IntelliSense обрабатывает документированное поле как `HTMLElement` при выполнении завершение операторов.  
  
 `mayBeNull`  
 Необязательный.  Определяет, является ли документированное поле можно указать значение NULL.  Установите значение `true`, чтобы указать, что поле можно указать значение NULL; в противном случае укажите значение `false`.  Значение по умолчанию — `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `elementType`  
 Необязательный.  Если `type` имеет значение `Array`, то этот атрибут определяет тип элементов в массиве.  
  
 `elementInteger`  
 Необязательный.  Если `type``Array` и `elementType``Number`, то этот атрибут определяет, является ли элементы массива целые числа.  Установите значение `true`, чтобы указать, что элементы массива целые числа; в противном случае укажите значение `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `elementDomElement`  
 Необязательный.  Этот атрибут выступан против; атрибут `elementType` имеет приоритет над этим атрибутом.  Если `type` имеет значение `Array`, то этот атрибут определяет, является ли элементы массива элементов DOM.  Задайте значение `true` для указания того, что элементы элементов DOM; в противном случае укажите значение `false`.  Если атрибут `elementType` не задан, а параметр `elementDomElement` имеет значение `true`, то IntelliSense обрабатывает каждый элемент массива как `HTMLElement` при выполнении завершение операторов.  
  
 `elementMayBeNull`  
 Необязательный.  Если свойство `type` имеет значение `Array`, указывает ли элементы массива можно задать значение NULL.  Установите значение `true`, чтобы указать, что элементы массива можно задать значение NULL; в противном случае укажите значение `false`.  Значение по умолчанию — `false`.  Этот атрибут не используется Visual Studio, чтобы предоставить сведения о технологии IntelliSense.  
  
 `helpKeyword`  
 Необязательный.  Ключевое слово для справки F1.  
  
 `locid`  
 Необязательный.  Идентификатор для данных о локализации поле.  Идентификатор или идентификатор элемента или он соответствует значению атрибута `name` в наборе сообщения, OpenAjax метаданными.  Тип идентификатора зависит от формата, указанного в теге [\<loc\>](../ide/loc-javascript.md).  
  
 `value`  
 Необязательный.  Указывает код, который должен использоваться для оценки для использования самого IntelliSense вместо кода функции.  Для `<field>`, этот атрибут поддерживается для функций конструктора, но не поддерживается для литералов объекта.  Этот атрибут можно использовать для предоставления сведений о типе, если тип поля не определен.  Например, можно использовать `value=’1’` для отрисовки тип поля в виде числа.  
  
 `description`  
 Необязательный.  Описание поля.  
  
## Заметки  
 Атрибут `name` является обязательным при документируете поле в конструктор.  Для всех других сценариев все атрибуты элемента `<field>` необязательно.  
  
 При документируете функцию конструктора, элемент `<field>` должен быть сразу после объявления полей.  Атрибут `name` должен соответствовать имени поля, используемого в исходном коде.  Для членов объектов атрибут `name` можно опустить, если элемент `<field>` отображается сразу после объявления объекта.  
  
## Пример  
 В следующем примере кода показано, как использовать элемент `<field>`.  
  
```javascript  
// Use of <field> in an object definition.  
var Rectangle = {  
    /// <field type='Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type='Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
  
// Use of <field> in a constructor function.  
// The name attribute is required.  
function Engine() {  
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
    this.HorsePower = 150;  
}  
```  
  
## Пример  
 В следующем примере показано, как использовать элемент `<field>`, атрибут `static` которого имеет значение `true`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## Пример  
 В следующем примере показано, как использовать элемент `<field>`, атрибут `static` которого имеет значение `false`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
var eng = new Engine();  
// IntelliSense on the field is available here.  
eng.  
  
```  
  
## Пример  
 В следующем примере показано, как использовать элемент `<field>` с атрибутом `value`.  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## См. также  
 [Комментарии XML\-документации](../ide/xml-documentation-comments-javascript.md)