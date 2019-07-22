---
title: '&lt;поле&gt; (JavaScript) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b2fe09070261460b7b83f54de44a07cf96d40cf2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181276"
---
# <a name="ltfieldgt-javascript"></a>&lt;поле&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает сведения о документации, включая описание, для поля или член, который определен для объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
#### <a name="parameters"></a>Параметры  
 `name`  
 Имя поля или член. Когда `<field>` элемент используется в функции конструктора, `name` является обязательным и определяет элемент, к которому применяется тега. Когда `<field>` элемент непосредственно Создание примечаний к полю, этот атрибут игнорируется и имени, используемой Visual Studio — это имя фактического поля в исходном коде.  
  
 `static`  
 Необязательный параметр. Определяет поле является членом функции-конструктора или член объекта, возвращаемый функцией-конструктором. Значение `true` следует считать поле является членом функции конструктора. Значение `false` следует считать поле является членом объекта, возвращаемого функции конструктора.  
  
 `type`  
 Необязательный параметр. Тип данных поля. Тип может быть одним из следующих:  
  
- Это язык на ECMAScript введите спецификацией ECMAScript 5, например `Number` и `Object`.  
  
- Объект DOM, например `HTMLElement`, `Window` и `Document`.  
  
- Функция конструктора JavaScript.  
  
  `integer`  
  Необязательный параметр. Если `type` является `Number`, указывает ли поле должно быть целым числом. Значение `true` для указания, что поле должно быть целым числом; в противном случае значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `domElement`  
  Необязательный параметр. Этот атрибут является устаревшим; атрибут `type` имеет приоритет над этим атрибутом. Этот атрибут указывает, является ли поле документированных DOM-элемента. Значение `true` для указания, что поле является элементом DOM; в противном случае значение `false`. Если `type` атрибут не задан и `domElement` присваивается `true`, IntelliSense считает поле документированных `HTMLElement` при выполнении завершения операторов.  
  
  `mayBeNull`  
  Необязательный параметр. Указывает, можно ли задать поле документированных в значение null. Значение `true` чтобы указать, что поле может быть установлено в значение null; в противном случае, значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `elementType`  
  Необязательный параметр. Если `type` является `Array`, этот атрибут указывает тип элементов в массиве.  
  
  `elementInteger`  
  Необязательный параметр. Если `type` — `Array`, а `elementType` — `Number`, этот атрибут указывает, являются ли элементы в массиве целыми числами. Значение `true` указывает, что элементы в массиве являются целыми числами; в противном случае — значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `elementDomElement`  
  Необязательный параметр. Этот атрибут является устаревшим; атрибут `elementType` имеет приоритет над этим атрибутом. Если `type` — `Array`, этот атрибут указывает, являются ли элементы в массиве элементами DOM. Значение `true` указывает, что элементы являются элементами DOM; в противном случае используется значение `false`. Если атрибут `elementType` не задан, а для `elementDomElement` установлено `true`, IntelliSense считает каждый элемент в массиве как `HTMLElement` при выполнении завершения операторов.  
  
  `elementMayBeNull`  
  Необязательный параметр. Если `type` является `Array`, указывает, могут ли элементы в массиве принимать значение NULL. Значение `true` указывает, что элементы в массиве могут принимать значение NULL; в противном случае — значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `helpKeyword`  
  Необязательный параметр. Ключевое слово для справки F1.  
  
  `locid`  
  Необязательный параметр. Идентификатор для локализации информацию о поле. Идентификатор является идентификатором члена или соответствует значению атрибута `name` в наборе сообщений, определенном метаданными OpenAjax. Тип идентификатора зависит от формата, указанного в теге [\<loc>](../ide/loc-javascript.md).  
  
  `value`  
  Необязательный параметр. Указывает код, который должен вычисляться для использования с IntelliSense вместо код самой функции. Для `<field>`, этот атрибут поддерживается для функции-конструкторы, но не поддерживается для объектных литералов. Можно использовать этот атрибут является для предоставления сведений о типе, если тип поля является неопределенным. Например, можно использовать `value=’1’` обрабатывать тип поля как число.  
  
  `description`  
  Необязательный параметр. Описание для поля.  
  
## <a name="remarks"></a>Примечания  
 `name` Атрибут является обязательным, если Документирование поле в функцию конструктора. Для всех других сценариев, все атрибуты `<field>` являются необязательными.  
  
 Если вы Документирование функция конструктора, `<field>` элемент должен находиться непосредственно перед объявлением поля. `name` Атрибута должно совпадать с именем поля, который используется в исходном коде. Для членов объекта `name` атрибута можно опустить, если `<field>` элемент появляется непосредственно перед объявлением члена объекта.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано использование элемента `<field>`.  
  
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
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать `<field>` элемент с `static` атрибут `true`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать `<field>` элемент с `static` атрибут `false`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
var eng = new Engine();  
// IntelliSense on the field is available here.  
eng.  
  
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать `<field>` элемент с `value` атрибута.  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>См. также  
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)
