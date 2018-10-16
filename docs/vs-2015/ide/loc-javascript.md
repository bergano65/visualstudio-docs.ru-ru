---
title: '&lt;Loc&gt; (JavaScript) | Документация Майкрософт'
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
- <loc> JavaScript XML tag
- loc JavaScript XML tag
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9314453b5e75e31f98d6989efa274278706bc5a4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244014"
---
# <a name="ltlocgt-javascript"></a>&lt;Loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает расположение и тип расширения файла, который содержит локализованные сведения IntelliSense.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<loc filename="filename"  
    format="vsdoc|messagebundle" />  
```  
  
#### <a name="parameters"></a>Параметры  
 `filename`  
 Необязательный. Имя корневого файла расширения, который содержит сведения о локализации для нейтрального языка и региональных параметров. Когда Visual Studio выполняет поиск сведений о локализации, предпринимается попытка найти региональных версию этого файла. Например если `filename` является jquery.xml, Visual Studio выполняет поиск нужную папку конкретного языка и региональных параметров (например, JA) в том же расположении, что js-файл, который содержит `<loc>` элемент. Он переходит на папку конкретного языка и региональных параметров, проверяет, существует ли файл jquery.xml в нем. Если он не может найти нужный файл, она использует правила расположения управляемых ресурсов. Значение по умолчанию для `filename` — это имя текущего файла, но с расширением XML вместо .js.  
  
 `format`  
 Необязательный. Тип расширения файла, используемого для локализации. Использовать `messagebundle` для указания использования пакеты сообщений определяются метаданные откройте Ajax. `messagebundle` — Это рекомендуемый формат. Тем не менее этот формат не поддерживается в Microsoft Ajax, или в файлах winmd. Используйте `vsdoc` для указания стандартного формата локализации .NET Framework, который используется Microsoft Ajax и средой выполнения Windows. Этот атрибут является необязательным. `vsdoc` является форматом по умолчанию.  
  
## <a name="remarks"></a>Примечания  
 `<loc>` Элемент должен отображаться в верхней части файла в тот же раздел `<reference>` элемент. Использование правил для `<loc>` элемент такие же, как `<reference>` элемент. Дополнительные сведения см. в разделе «Директивы ссылки» в [IntelliSense для JavaScript](../ide/javascript-intellisense.md).  
  
 Visual Studio обрабатывает один `<loc>` элемент для каждого JS-файла. При наличии нескольких `<loc>` элементы присутствуют, только один `<loc>` используется элемент. Поведение по выбору `<loc>` элемент не определен.  
  
 При использовании формата пакета сообщений, используйте `locid` атрибут в комментарии XML-документации, чтобы указать `name` значение атрибута.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать `<loc>` элемент messagebundle формате. Добавьте следующий код XML в файл с именем messageFilename.xml и поместить его в соответствующую папку конкретного языка и региональных параметров, как указано в описании `filename` параметра.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<messagebundle>  
  <msg name="1">A class that represents a rectangle</msg>  
  <msg name="2">The height of a rectangle</msg>  
  <msg name="3">The width of a rectangle</msg>  
</messagebundle>  
  
```  
  
 Например messagebundle добавьте следующий код в файл JavaScript в проекте. `<loc>` Должен отображаться в качестве первой строки в файле JavaScript. Описания в этом коде будет заменен локализованного описания, если он доступен.  
  
```javascript  
/// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
function doSomething(a,b)   
{  
    /// <summary locid='1'>description</summary>  
    /// <param name='a' locid='2'>parameter a description</param>  
    /// <param name='b' locid='3'>parameter b description</param>  
}  
  
```  
  
 В следующем примере используется формат VSDoc. Добавьте следующий код XML в файл с именем scriptFilename.xml и поместить его в соответствующую папку конкретного языка и региональных параметров.  
  
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
  
 Например VSDoc добавьте следующий код в файл JavaScript в проекте. Описания в этом коде будет заменен локализованного описания, если он доступен.  
  
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



