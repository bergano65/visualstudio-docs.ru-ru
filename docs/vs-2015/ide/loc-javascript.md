---
title: '&lt;Loc &gt; (JavaScript) | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651477"
---
# <a name="ltlocgt-javascript"></a>&lt;Loc &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Задает расположение и тип файла расширения, который предоставляет локализованные сведения об IntelliSense.

## <a name="syntax"></a>Синтаксис

```
<loc filename="filename"
    format="vsdoc|messagebundle" />
```

#### <a name="parameters"></a>Параметры
 `filename` Необязательный. Корневое имя файла расширения, содержащего сведения о локализации для нейтрального языка и региональных параметров. Когда Visual Studio выполняет поиск сведений о локализации, он пытается найти версию этого файла, относящуюся к языку и региональным параметрам. Например, если `filename` имеет значение jquery.xml, Visual Studio ищет правильную папку, зависящую от языка и региональных параметров (например, JA), в том же расположении, что и JS-файл, содержащий `<loc>` элемент. Если путь к папке зависит от языка и региональных параметров, он проверяет, существует ли в нем файл jquery.xml. Если не удается выбрать правильный файл, вместо этого используются правила расположения управляемых ресурсов. Значение по умолчанию для `filename` — это имя текущего файла, но с расширением XML вместо. js.

 `format` Необязательный. Тип файла расширения, используемого для локализации. Используется `messagebundle` для указания использования пакетов сообщений, определенных открытыми метаданными AJAX. `messagebundle` Рекомендуемый формат. Однако этот формат не поддерживается в Microsoft AJAX или в WinMD-файлах. Используется `vsdoc` для указания стандартного формата локализации .NET Framework, используемого в Microsoft AJAX и среда выполнения Windows. Этот атрибут является необязательным. `vsdoc` является форматом по умолчанию.

## <a name="remarks"></a>Remarks
 `<loc>`Элемент должен находиться в верхней части файла в том же разделе, что и `<reference>` элемент. Правила использования элемента совпадают с правилами `<loc>` `<reference>` элемента. Дополнительные сведения см. в подразделе "директивы References" статьи [IntelliSense JavaScript](../ide/javascript-intellisense.md).

 Visual Studio обрабатывает один `<loc>` элемент для каждого JS-файла. Если `<loc>` имеется несколько элементов, то используется только один `<loc>` элемент. Поведение при определении используемого `<loc>` элемента не определено.

 При использовании формата пакета сообщений используйте `locid` атрибут в комментариях XML-документации, чтобы указать `name` значение атрибута.

## <a name="example"></a>Пример
 В следующем примере показано, как использовать `<loc>` элемент с форматом мессажебундле. Добавьте следующий XML-код в файл с именем messageFilename.xml и поместите его в соответствующую папку, зависящую от языка и региональных параметров, как указано в описании `filename` параметра.

```
<?xml version="1.0" encoding="utf-8" ?>
<messagebundle>
  <msg name="1">A class that represents a rectangle</msg>
  <msg name="2">The height of a rectangle</msg>
  <msg name="3">The width of a rectangle</msg>
</messagebundle>

```

 В примере мессажебундле добавьте следующий код в файл JavaScript в проекте. `<loc>`Элемент должен отображаться в виде первой строки в файле JavaScript. Описания в этом коде будут заменены локализованными описаниями, если они доступны.

```javascript
/// <loc filename="messageFilename.xml" format="messagebundle"/>

function doSomething(a,b)
{
    /// <summary locid='1'>description</summary>
    /// <param name='a' locid='2'>parameter a description</param>
    /// <param name='b' locid='3'>parameter b description</param>
}

```

 В следующем примере используется формат Всдок. Добавьте следующий XML-код в файл с именем scriptFilename.xml и поместите его в соответствующую папку, относящуюся к языку и региональным параметрам.

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

## <a name="see-also"></a>См. также:
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)
