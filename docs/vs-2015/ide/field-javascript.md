---
title: '&lt;поле&gt; (JavaScript) | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 52f9c4ffef27b7b17bbcb75d734b4d0b7e41a3ff
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271652"
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
 Необязательный. Определяет поле является членом функции-конструктора или член объекта, возвращаемый функцией-конструктором. Значение `true` следует считать поле является членом функции конструктора. Значение `false` следует считать поле является членом объекта, возвращаемого функции конструктора.  
  
 `type`  
 Необязательный. Тип данных поля. Тип может принимать одно из следующих значений:  
  
-   Это язык на ECMAScript введите спецификацией ECMAScript 5, например `Number` и `Object`.  
  
-   Объект DOM, таких как `HTMLElement`, `Window`, и `Document`.  
  
-   Функция конструктора, JavaScript.  
  
 `integer`  
 Необязательный. Если `type` является `Number`, указывает ли поле должно быть целым числом. Значение `true` для указания, что поле должно быть целым числом; в противном случае значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
 `domElement`  
 Необязательный. Этот атрибут является устаревшим; `type` атрибут имеет приоритет над этот атрибут. Этот атрибут указывает, является ли поле документированных DOM-элемента. Значение `true` для указания, что поле является элементом DOM; в противном случае значение `false`. Если `type` атрибут не задан и `domElement` присваивается `true`, IntelliSense считает поле документированных `HTMLElement` при выполнении завершения операторов.  
  
 `mayBeNull`  
 Необязательный. Указывает, можно ли задать поле документированных в значение null. Значение `true` чтобы указать, что поле может быть установлено в значение null; в противном случае, значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
 `elementType`  
 Необязательный. Если `type` является `Array`, этот атрибут указывает тип элементов в массиве.  
  
 `elementInteger`  
 Необязательный. Если `type` — `Array` и `elementType` является `Number`, этот атрибут указывает, являются ли элементы в массив целых чисел. Значение `true` для указания, представляют собой целые числа элементов в массиве; в противном случае — значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
 `elementDomElement`  
 Необязательный. Этот атрибут является устаревшим; `elementType` атрибут имеет приоритет над этот атрибут. Если `type` является `Array`, этот атрибут указывает, являются ли элементы в массиве элементов DOM. Значение `true` для указания, элементы являются элементами DOM; в противном случае — значение `false`. Если `elementType` атрибут не задан и `elementDomElement` присваивается `true`, IntelliSense обрабатывает каждый элемент массива в виде `HTMLElement` при выполнении завершения операторов.  
  
 `elementMayBeNull`  
 Необязательный. Если `type` является `Array`, указывает ли элементы в массиве можно задать значение null. Значение `true` чтобы указать, что элементы в массиве может быть установлен в значение null; в противном случае, значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
 `helpKeyword`  
 Необязательный. Ключевое слово для справки F1.  
  
 `locid`  
 Необязательный. Идентификатор для локализации информацию о поле. Идентификатор является либо член идентификатор или он соответствует `name` значение в набор сообщений, определяется альянсе метаданных атрибута. Тип идентификатора зависит от формата, указанного в [ \<loc >](../ide/loc-javascript.md) тега.  
  
 `value`  
 Необязательный. Указывает код, который должен вычисляться для использования с IntelliSense вместо код самой функции. Для `<field>`, этот атрибут поддерживается для функции-конструкторы, но не поддерживается для объектных литералов. Можно использовать этот атрибут является для предоставления сведений о типе, если тип поля является неопределенным. Например, можно использовать `value=’1’` обрабатывать тип поля как число.  
  
 `description`  
 Необязательный. Описание для поля.  
  
## <a name="remarks"></a>Примечания  
 `name` Атрибут является обязательным, если Документирование поле в функцию конструктора. Для всех других сценариев, все атрибуты `<field>` являются необязательными.  
  
 Если вы Документирование функция конструктора, `<field>` элемент должен находиться непосредственно перед объявлением поля. `name` Атрибута должно совпадать с именем поля, который используется в исходном коде. Для членов объекта `name` атрибута можно опустить, если `<field>` элемент появляется непосредственно перед объявлением члена объекта.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как использовать `<field>` элемент.  
  
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



