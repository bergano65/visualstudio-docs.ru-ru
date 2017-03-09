---
title: "&lt;loc&gt; (JavaScript) | Microsoft Docs"
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
  - "XML-тег JavaScript <loc>"
  - "loc - XML-тег JavaScript"
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Указывает расположение и тип файла sidecar, предоставляет локализованные данные IntelliSense.  
  
## Синтаксис  
  
```  
<loc filename="filename"  
    format="vsdoc|messagebundle" />  
```  
  
#### Параметры  
 `filename`  
 Необязательный.  Sidecar корневое имя файла, содержащего данные о локализации для нейтрального языка и региональных параметров.  При поиске Visual Studio для данных локализации, он пытается найти версию языка и региональных параметров этого файла.  Например, если `filename` jquery.xml, поиск Visual Studio для соответствующей папки для конкретных языков и региональных параметров \(например, JA\) в той же папке, что и файл .js, содержащий элемент `<loc>`.  Если он определяет папку для конкретных языков и региональных параметров, он проверяет, существует ли файл jquery.xml в нем.  Если оно не может найти правильный файл, вместо этого он использует правила расположения управляемых ресурсов.  Значение по умолчанию для свойства `filename` имя текущего файла, но с расширением XML вместо .js.  
  
 `format`  
 Необязательный.  Тип файла sidecar, используемый для локализации.  С помощью атрибута `messagebundle` задать использование набора сообщений, метаданными Open Ajax.  рекомендуемый формат `messagebundle`.  Однако этот формат не поддерживается в Microsoft Ajax или в файлах .winmd.  Используйте `vsdoc`, чтобы указать формат локализации .NET Framework стандарта, используемый Microsoft Ajax и Среда выполнения Windows.  Этот атрибут является необязательным.  формат `vsdoc` по умолчанию.  
  
## Заметки  
 Элемент `<loc>` должен отображаться в верхней части файла в одном разделе, элемент `<reference>`.  Правила потребления для элемента `<loc>` совпадает с элементом `<reference>`.  Дополнительные сведения см. в разделе «\- директивы» раздела [IntelliSense для JavaScript](../ide/javascript-intellisense.md).  
  
 Процессы Visual Studio один элемент `<loc>` для каждого файла с расширением .js.  Если несколько элементов `<loc>` отсутствуют, то используется только один элемент `<loc>`.  Расширение функциональности для определения элемента `<loc>`, который будет использоваться не определены.  
  
 При использовании формата набора сообщений, используйте атрибут `locid` в комментарии XML\-документации для указания значения атрибута `name`.  
  
## Пример  
 В следующем примере показано использование элемента `<loc>` с форматом messagebundle.  Добавьте следующий XML\-код в файл messageFilename.xml и поместите файл в нужной папке языка и региональных параметров, заданному в описании параметра `filename`.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<messagebundle>  
  <msg name="1">A class that represents a rectangle</msg>  
  <msg name="2">The height of a rectangle</msg>  
  <msg name="3">The width of a rectangle</msg>  
</messagebundle>  
  
```  
  
 Пример messagebundle, добавьте следующий код в файл JavaScript в проекте.  Элемент `<loc>` должен выглядеть как первая линия в файле JavaScript.  Описание в этом коде будут заменены локализованными описаниями, если это возможно.  
  
```javascript  
/// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
function doSomething(a,b)   
{  
    /// <summary locid='1'>description</summary>  
    /// <param name='a' locid='2'>parameter a description</param>  
    /// <param name='b' locid='3'>parameter b description</param>  
}  
  
```  
  
 В следующем примере используется формат VSDoc.  Добавьте следующий XML\-код в файл scriptFilename.xml и поместите файл в нужной папке языка и региональных параметров.  
  
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
  
 Пример VSDoc, добавьте следующий код в файл JavaScript в проекте.  Описание в этом коде будут заменены локализованными описаниями, если это возможно.  
  
```javascript  
/// <loc filename="scriptFilename.xml" format="vsdoc" />  
  
function illuminate(a)   
{  
    /// <summary locid='M:illuminate'>description</summary>  
    /// <param name='a' type='Number'>parameter a description</param>  
}  
  
```  
  
## См. также  
 [Комментарии XML\-документации](../ide/xml-documentation-comments-javascript.md)