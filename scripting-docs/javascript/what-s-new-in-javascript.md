---
title: "Новые возможности JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 342b68ef-df93-48c4-81de-bdf6b6ce58d9
caps.latest.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 33
---
# Новые возможности JavaScript
В этом документе перечислены новые функции JavaScript, которые поддерживаются в [режиме границ](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx), [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)], и приложениях Магазина Windows Phone.  
  
 Сведения об элементах JavaScript, которые поддерживаются в режиме границ, но не рекомендованы к использованию в приложениях [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)], см. в разделе [Сведения о версии](../javascript/reference/javascript-version-information.md).  
  
> [!IMPORTANT]
>  Сведения о создании приложений [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] и приложений Магазина Windows Phone с помощью JavaScript, включая сведения о редакторе JavaScript Visual Studio и других компонентах, см. в статье [Разработка приложений с помощью Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkID=238263).  
  
## Новые функции в JavaScript  
  
|Функция|Описание|  
|-------------|--------------|  
|Классы|Новый синтаксис поддерживает объявление [классов](../javascript/reference/class-statement-javascript.md).|  
|Обещания|[Обещания](../javascript/reference/promise-object-javascript.md) упрощают создание асинхронного кода и позволяют создавать более чистый код.  Конструкторы обещаний поддерживаются вместе со служебными методами `all` и `race`.|  
|Итераторы|Теперь можно выполнить итерацию поддерживающих итерацию объектов \(включая массивы, объекты, похожие на массивы, и итераторы\), вызывая пользовательский обработчик итераций с операторами, которые должны быть исполнены для значения каждого свойства по отдельности.  Дополнительные сведения см. в разделе [Итераторы и генераторы](../javascript/advanced/iterators-and-generators-javascript.md). **Note:**  Генераторы пока не поддерживаются.|  
|Функции со стрелкой|Функция со стрелкой \(\=\>\) предоставляет сокращенный синтаксис для ключевого слова `function` с лексической привязкой `this`.|  
|Новые методы для встроенных объектов|Встроенные объекты [Объект Array](../javascript/reference/array-object-javascript.md), [Объект Math](../javascript/reference/math-object-javascript.md), [Объект Number](../javascript/reference/number-object-javascript.md), [Объект Object](../javascript/reference/object-object-javascript.md) и [Объект String](../javascript/reference/string-object-javascript.md) предоставляют множество новых служебных функций и свойств для обработки и инспектирования данных.|  
|Усовершенствования литерала объекта|Объекты теперь поддерживают вычисляемые свойства, точные определения методов и сокращенный синтаксис для свойств, значения которых инициализируются в переменную с таким же именем.  Дополнительные сведения см. в разделе [Создание объектов](../javascript/creating-objects-javascript.md).|  
|Прокси\-элементы|Благодаря [прокси\-элементам](../javascript/reference/proxy-object-javascript.md) становится возможным пользовательское поведение объектов.|  
|Параметры Rest|Параметры Rest позволяют преобразовать последовательные аргументы в вызове функции в массив.  Дополнительные сведения см. в разделе [Функции](../javascript/functions-javascript.md).|  
|Оператор Spread|[Оператор spread](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md) \(`…`\) расширяет доступные для итерации выражения в отдельные аргументы.  Например, `a.b(…array)` примерно равен `a.b.apply(a, array)`.|  
|Символы|Объекты [Symbol](../javascript/reference/symbol-object-javascript.md) позволяют добавлять свойства в существующие объекты, исключая возможность создания помех существующим свойствам объектов, без непредусмотренной видимости и других несогласованных дополнений, которые могут быть реализованы другими частями кода.|  
|Строки шаблона|[Строки шаблона](../javascript/advanced/template-strings-javascript.md) — это строковые литералы, позволяющие оценивать выражения и сцеплять их со строковым литералом.|  
|Усовершенствования Юникода|Была усовершенствована поддержка Юникода.  Так, новый формат escape\-последовательности поддерживает астральные кодовые точки \(кодовые точки с более 4 шестнадцатеричных цифр\).  Дополнительные сведения см. в разделе [Специальные символы](../javascript/advanced/special-characters-javascript.md).|  
|Множество WeakSet|Множество [WeakSet](../javascript/reference/weakset-object-javascript.md) представляет собой коллекцию объектов, которая будет удалена как мусор, если на нее отсутствуют ссылки в каком\-либо другом месте.|  
  
## См. также  
 [Справочник по языку JavaScript](../javascript/javascript-language-reference.md)