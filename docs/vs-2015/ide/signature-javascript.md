---
title: '&gt; &lt;signature (JavaScript) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4c640c28ada16a8a03943fcd1362d4fd521772c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671132"
---
# <a name="ltsignaturegt-javascript"></a>&gt; &lt;signature (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Группирует набор связанных элементов для функции или метода, чтобы предоставить документацию по перегруженным функциям.

## <a name="syntax"></a>Синтаксис

```
<signature externalid="id" externalFile="filename"
    helpKeyword="keyword" locid="descriptionID">
</signature>
```

#### <a name="parameters"></a>Параметры
 `externalid` Необязательный. Если атрибут `format` для \<loc элемента [>](../ide/loc-javascript.md) `vsdoc`, этот атрибут указывает идентификатор элемента, используемый для размещения XML-кода, связанного с сигнатурой. В отличие от атрибута `locid`, этот атрибут указывает, что все элементы в члене, имеющие этот идентификатор, должны быть загружены. Все связанные сведения о описании, представленные в XML-коде, также будут объединены с элементами, указанными в сигнатуре. Это позволяет указать дополнительные элементы, например `<capability>`, в файле расширения, не указывая их в исходном файле. `externalid` является необязательным атрибутом.

 `externalFile` Необязательный. Указывает имя файла, в котором нужно найти `externalid`. Этот атрибут пропускается, если `externalid` отсутствует. Это необязательный атрибут. Значение по умолчанию — это имя текущего файла, но с расширением. XML вместо. js. По умолчанию для поиска файла используются правила подстановки управляемых ресурсов для локализации.

 `helpKeyword` Необязательный. Ключевое слово для справки F1.

 `locid` Необязательный. Идентификатор для сведений о локализации поля. Идентификатор является идентификатором члена или соответствует значению атрибута `name` в наборе сообщений, определенном метаданными OpenAjax. Тип идентификатора зависит от формата, указанного в теге [\<loc>](../ide/loc-javascript.md).

## <a name="remarks"></a>Примечания
 Используйте один элемент `<signature>` для каждого описания перегруженной функции в JS файл или используйте один элемент `<signature>` для каждого указанного идентификатора внешнего элемента.

 Элемент `<signature>` должен быть помещен в тело функции перед любыми инструкциями. При использовании [\<summary >](../ide/summary-javascript.md), [\<param >](../ide/param-javascript.md)или [\<returns >](../ide/returns-javascript.md) элементов с помощью элемента `<signature>` поместите другие элементы внутри блока `<signature>`.

## <a name="example"></a>Пример
 В следующем примере кода показано использование элемента `<signature>`.

```javascript
// Use of <signature> with externalid.
// Requires use of the <loc> tag to identify the external functions.
function illuminate(light) {
    /// <signature externalid='M:Windows.Devices.Light.Illuminate()' />
    /// <signature externalid='M:Windows.Devices.Light.Illuminate(System.Int32)'>
    ///   <param name='light' type='Number' />
    /// </signature>
}

// Use of <signature> for overloads implemented in JavaScript.
function add(a, b) {
    /// <signature>
    /// <summary>function summary 1</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 2 – differ by number of params</summary>
    /// <param name="a" type="Number">Only 1 parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 3 – differ by parameter type</summary>
    /// <param name="a" type="Number">Number parameter</param>
    /// <param name="b" type="String">String parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 4 – differ by return type</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="String" />
    /// </signature>

    return a + b;
}
```

## <a name="see-also"></a>См. также
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)
