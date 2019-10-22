---
title: '&gt; &lt;loc (JavaScript) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <loc> JavaScript XML tag
- loc JavaScript XML tag
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf6016b2c12fd5ebe7cfb76c14c776508d99d2db
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651477"
---
# <a name="ltlocgt-javascript"></a>&gt; &lt;loc (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Задает расположение и тип файла расширения, который предоставляет локализованные сведения об IntelliSense.

## <a name="syntax"></a>Синтаксис

```
<loc filename="filename"
    format="vsdoc|messagebundle" />
```

#### <a name="parameters"></a>Параметры
 `filename` Необязательный. Корневое имя файла расширения, содержащего сведения о локализации для нейтрального языка и региональных параметров. Когда Visual Studio выполняет поиск сведений о локализации, он пытается найти версию этого файла, относящуюся к языку и региональным параметрам. Например, если `filename` имеет значение jQuery. XML, Visual Studio ищет правильную папку для конкретного языка и региональных параметров (например, JA) в том же расположении, что и JS-файл, содержащий элемент `<loc>`. Если путь к папке зависит от языка и региональных параметров, он проверяет, существует ли в нем файл jQuery. XML. Если не удается выбрать правильный файл, вместо этого используются правила расположения управляемых ресурсов. Значение по умолчанию для `filename` — имя текущего файла, но с расширением XML вместо. js.

 `format` Необязательный. Тип файла расширения, используемого для локализации. Используйте `messagebundle`, чтобы указать использование пакетов сообщений, определенных открытыми метаданными AJAX. Рекомендуемый формат — `messagebundle`. Однако этот формат не поддерживается в Microsoft AJAX или в WinMD-файлах. Используйте `vsdoc`, чтобы указать стандартный формат локализации .NET Framework, используемый в Microsoft AJAX и среда выполнения Windows. Этот атрибут является необязательным. `vsdoc` является форматом по умолчанию.

## <a name="remarks"></a>Примечания
 Элемент `<loc>` должен находиться в верхней части файла в том же разделе, что и элемент `<reference>`. Правила использования элемента `<loc>` совпадают с `<reference>`ным элементом. Дополнительные сведения см. в подразделе "директивы References" статьи [IntelliSense JavaScript](../ide/javascript-intellisense.md).

 Visual Studio обрабатывает один элемент `<loc>` для каждого JS-файла. Если имеется несколько элементов `<loc>`, то используется только один элемент `<loc>`. Поведение при определении того, какой элемент `<loc>` следует использовать, не определен.

 При использовании формата пакета сообщений используйте атрибут `locid` в комментариях XML-документации, чтобы указать значение атрибута `name`.

## <a name="example"></a>Пример
 В следующем примере показано, как использовать элемент `<loc>` с форматом мессажебундле. Добавьте следующий XML-код в файл с именем Мессажефиленаме. XML и поместите его в соответствующую папку, зависящую от языка и региональных параметров, как указано в описании параметра `filename`.

```
<?xml version="1.0" encoding="utf-8" ?>
<messagebundle>
  <msg name="1">A class that represents a rectangle</msg>
  <msg name="2">The height of a rectangle</msg>
  <msg name="3">The width of a rectangle</msg>
</messagebundle>

```

 В примере мессажебундле добавьте следующий код в файл JavaScript в проекте. Элемент `<loc>` должен отображаться в виде первой строки в файле JavaScript. Описания в этом коде будут заменены локализованными описаниями, если они доступны.

```javascript
/// <loc filename="messageFilename.xml" format="messagebundle"/>

function doSomething(a,b)
{
    /// <summary locid='1'>description</summary>
    /// <param name='a' locid='2'>parameter a description</param>
    /// <param name='b' locid='3'>parameter b description</param>
}

```

 В следующем примере используется формат Всдок. Добавьте следующий XML-код в файл с именем Скриптфиленаме. XML и поместите его в соответствующую папку, относящуюся к языку и региональным параметрам.

```
<?xml version="1.0" encoding="utf-8" ?>
<doc>
  <assembly>
    <name>Lights</name>
  </assembly>
  <members>
    <member name="M:illuminate">
      <summary>Activates a light. </summary>
      <param name='a'>The light to activate. </param>
    </member>
  </members>
</doc>

```

 В примере Всдок добавьте следующий код в файл JavaScript в проекте. Описания в этом коде будут заменены локализованными описаниями, если они доступны.

```javascript
/// <loc filename="scriptFilename.xml" format="vsdoc" />

function illuminate(a)
{
    /// <summary locid='M:illuminate'>description</summary>
    /// <param name='a' type='Number'>parameter a description</param>
}

```

## <a name="see-also"></a>См. также
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)
