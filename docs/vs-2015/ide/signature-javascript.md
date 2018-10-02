---
title: '&lt;подпись&gt; (JavaScript) | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5b6172609b68e1800dd71b9367d93a52596e88cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557554"
---
# <a name="ltsignaturegt-javascript"></a>&lt;подпись&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [документация по Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
Группирует набор связанных элементов для функции или метода документации для перегруженных функций.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<signature externalid="id" externalFile="filename"  
    helpKeyword="keyword" locid="descriptionID">  
</signature>   
```  
  
#### <a name="parameters"></a>Параметры  
 `externalid`  
 Необязательный. Если `format` для атрибута [ \<loc >](../ide/loc-javascript.md) элемент является `vsdoc`, этот атрибут указывает элемент, идентификатор, используемый для поиска XML-код, который связан с сигнатурой. В отличие от `locid` атрибут, этот атрибут указывает, что должны загружаться все элементы в элемент с этим Идентификатором. Также любое связанное описание сведений, представленных в XML-коде будут объединены с элементами, указанными в сигнатуре. Это позволяет указать дополнительные элементы, такие как `<capability>`, в файле расширения без указания их в исходном файле. `externalid` является необязательным атрибутом.  
  
 `externalFile`  
 Необязательный. Указывает имя файла, в котором осуществляется поиск `externalid`. Этот атрибут учитывается, если не `externalid` присутствует. Это необязательный атрибут. Значение по умолчанию — имя текущего файла, но с расширением .xml вместо .js. По умолчанию правила поиска управляемых ресурсов для локализации используются для поиска файла.  
  
 `helpKeyword`  
 Необязательный. Ключевое слово для справки F1.  
  
 `locid`  
 Необязательный. Идентификатор для локализации информацию о поле. Идентификатор является либо член идентификатор или он соответствует `name` значение в набор сообщений, определяется альянсе метаданных атрибута. Тип идентификатора зависит от формата, указанного в [ \<loc >](../ide/loc-javascript.md) тега.  
  
## <a name="remarks"></a>Примечания  
 Используйте один `<signature>` для каждого элемента перегружены описание функции в JS-файл или использовать один `<signature>` элемент для каждого идентификатора внешнего члена, указанного.  
  
 `<signature>` Элемент должен быть помещен в тело функции до всех операторов. При использовании [ \<summary >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), или [ \<возвращает >](../ide/returns-javascript.md) элементов при помощи `<signature>` элемент, расположение других элементов внутри `<signature>` блока.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как использовать `<signature>` элемент.  
  
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



