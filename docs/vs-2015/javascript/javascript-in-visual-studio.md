---
title: JavaScript
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-javascript
ms.topic: conceptual
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14da091149f44d185d783c071f67294b7d2431e6
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58195025"
---
# <a name="javascript-in-visual-studio"></a>JavaScript в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript — полноправный язык в Visual Studio. При написании кода JavaScript в интегрированной среде разработки Visual Studio можно использовать большинство или все стандартные средства редактирования (фрагменты кода, IntelliSense и т. д.). Код JavaScript можно написать для многих типов приложений и служб.

 См. справочную документацию по языку [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Определенные версии Visual Studio или специальные расширения Visual Studio могут потребоваться для разработки конкретных типов приложений и служб с помощью HTML и JavaScript. В следующем списке приводятся ссылки на дополнительные сведения.

- Для создания кроссплатформенных приложений с помощью Apache Cordova [доступны средства Visual Studio для Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606).

- Для создания приложений для платформ [Магазин Windows](http://dev.windows.com/develop) и [Windows Phone](http://dev.windows.com/develop) (а также универсальных приложений с поддержкой двух этих платформ) [доступны эти средства](https://developer.microsoft.com/windows/downloads).

- Для создания облачных служб посетите [сайт Microsoft Azure](http://azure.microsoft.com/documentation/).

- Для создания веб-сайтов и веб-приложений посетите [сайт ASP.NET](http://www.asp.net/get-started/websites).

  > [!NOTE]
  >  Можно создать пустой веб-сайт ASP.NET и использовать его для программирования кода HTML, CSS и JavaScript. Файл Webconfig, предоставляемый ASP.NET, дает возможность выполнять отладку в Visual Studio (кроме того, при запуске приложения можно использовать инструменты F12).

  Редактор JavaScript в Visual Studio обеспечивает поддержку IntelliSense. См. дополнительные сведения об [IntelliSense для JavaScript](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Новые возможности JavaScript
 Новые функции для JavaScript перечислены в следующей таблице.

|Функция|Описание|
|-------------|-----------------|
|Классы|Новый синтаксис поддерживает объявление [классов](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/class).|
|Обещания|[Обещания](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) упрощают создание асинхронного и более чистого кода. Конструкторы обещаний поддерживаются вместе со служебными методами `all` и `race`.|
|Итераторы|Теперь можно выполнить итерацию поддерживающих итерацию объектов (включая массивы, объекты, похожие на массивы, и итераторы), вызывая пользовательский обработчик итераций с операторами, которые должны быть исполнены для значения каждого свойства по отдельности. См. дополнительные сведения см. об [итераторах и генераторах](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators). **Примечание.** Генераторы пока не поддерживаются.|
|Функции со стрелкой|Функция со стрелкой (=>) предоставляет сокращенный синтаксис для ключевого слова `function` с лексической привязкой `this`.|
|Новые методы для встроенных объектов|Встроенные объекты [Array Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array), [Math Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math), [Number Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), [Object Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object) и [String Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) предоставляют множество новых служебных функций и свойств для обработки и инспектирования данных.|
|Усовершенствования объектного литерала|Объекты теперь поддерживают вычисляемые свойства, точные определения методов и сокращенный синтаксис для свойств, значения которых инициализируются в переменную с таким же именем. См. дополнительные сведения о [создании объектов](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object).|
|Прокси-элементы|[Прокси-элементы](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy) позволяют настраивать пользовательское поведение объектов.|
|Параметры Rest|Параметры Rest позволяют преобразовать последовательные аргументы в вызове функции в массив. См. дополнительные сведения о [функциях](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function).|
|Оператор Spread|[Оператор spread](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_operator) (`…`) расширяет доступные для итерации выражения в отдельные аргументы. Например, `a.b(…array)` примерно равен `a.b.apply(a, array)`.|
|Символы|Объекты [Symbol](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol) позволяют добавлять свойства в существующие объекты без создания помех существующим свойствам объектов, непредусмотренной видимости и других несогласованных дополнений, которые могут быть реализованы другими частями кода.|
|Строки шаблона|[Строки шаблона](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals) — это строковые литералы, позволяющие оценивать выражения и сцеплять их со строковым литералом.|
|Усовершенствования Юникода|Была усовершенствована поддержка Юникода. Так, новый формат escape-последовательности поддерживает астральные кодовые точки (кодовые точки с более 4 шестнадцатеричных цифр). См. дополнительные сведения о [специальных символах](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#Types_of_special_characters).|
|Множество WeakSet|Множество [WeakSet](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) — это коллекция объектов, которая будет удалена как мусор при отсутствии доступных ссылок на нее.|
