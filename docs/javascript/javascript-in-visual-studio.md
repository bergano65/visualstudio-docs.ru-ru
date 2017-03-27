---
title: "JavaScript в Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 77e7ce26df70e41e2328442454fe78c7a663f1f3
ms.openlocfilehash: de00ef86413571739446b61427c3a8e6c4680c06
ms.lasthandoff: 03/08/2017

---
# <a name="javascript-in-visual-studio"></a>JavaScript в Visual Studio
JavaScript — полноправный язык в Visual Studio. При написании кода JavaScript в интегрированной среде разработки Visual Studio можно использовать большинство или все стандартные средства редактирования (фрагменты кода, IntelliSense и т. д.). Код JavaScript можно написать для многих типов приложений и служб.  
  
 См. справочную документацию по языку [JavaScript](https://docs.microsoft.com/scripting/javascript/javascript-language-reference).
  
 Определенные версии Visual Studio или специальные расширения Visual Studio могут потребоваться для разработки конкретных типов приложений и служб с помощью HTML и JavaScript. В следующем списке приводятся ссылки на дополнительные сведения.  
  
-   Для создания кроссплатформенных приложений с помощью Apache Cordova [доступны средства Visual Studio для Apache Cordova](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/).  
  
-   Ссылки на технологии JavaScript, которые можно использовать в Visual Studio, вы найдете на страницах описания [JavaScript](https://docs.microsoft.com/scripting/javascript/) и [технологий создания скриптов](https://docs.microsoft.com/scripting/).
  
 Редактор JavaScript в Visual Studio обеспечивает поддержку IntelliSense. См. дополнительные сведения об [IntelliSense для JavaScript](../ide/javascript-intellisense.md).  
  
## <a name="whats-new-in-javascript"></a>Новые возможности JavaScript  
 Новые функции для JavaScript перечислены в следующей таблице.  
  
|Функция|Описание|  
|-------------|-----------------|  
|Классы|Новый синтаксис поддерживает объявление [классов](http://msdn.microsoft.com/Library/bf45ebad-4678-4062-88df-55d32b603c69).|  
|Обещания|[Обещания](http://msdn.microsoft.com/Library/358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6) упрощают создание асинхронного и более чистого кода. Конструкторы обещаний поддерживаются вместе со служебными методами `all` и `race`.|  
|Итераторы|Теперь можно выполнить итерацию поддерживающих итерацию объектов (включая массивы, объекты, похожие на массивы, и итераторы), вызывая пользовательский обработчик итераций с операторами, которые должны быть исполнены для значения каждого свойства по отдельности. См. дополнительные сведения см. об [итераторах и генераторах](http://msdn.microsoft.com/Library/68ef5b2f-0349-492b-b557-73ff2a2f90cf). **Примечание.** Генераторы пока не поддерживаются.|  
|Функции со стрелкой|Функция со стрелкой (=>) предоставляет сокращенный синтаксис для ключевого слова `function` с лексической привязкой `this`.|  
|Новые методы для встроенных объектов|Встроенные объекты [Array Object](http://msdn.microsoft.com/Library/08e5f552-0797-4b48-8164-609582fc18c9), [Math Object](http://msdn.microsoft.com/Library/607b94cb-921c-43cd-b514-fdbc13aeced6), [Number Object](http://msdn.microsoft.com/Library/76e87c37-cf6c-46cc-bafa-04be1fe3d78d), [Object Object](http://msdn.microsoft.com/Library/d24ef8fc-217b-4828-94e1-19f72780bae0) и [String Object](http://msdn.microsoft.com/Library/8063ecd5-5778-4e87-b985-b21420171914) предоставляют множество новых служебных функций и свойств для обработки и инспектирования данных.|  
|Усовершенствования объектного литерала|Объекты теперь поддерживают вычисляемые свойства, точные определения методов и сокращенный синтаксис для свойств, значения которых инициализируются в переменную с таким же именем. См. дополнительные сведения о [создании объектов](http://msdn.microsoft.com/Library/58d1baa5-4fe8-4a56-a926-5b11765df704).|  
|Прокси-элементы|[Прокси-элементы](http://msdn.microsoft.com/Library/2b89abee-04fa-47e6-9676-980016cff5f8) позволяют настраивать пользовательское поведение объектов.|  
|Параметры Rest|Параметры Rest позволяют преобразовать последовательные аргументы в вызове функции в массив. См. дополнительные сведения о [функциях](http://msdn.microsoft.com/Library/e2a72b5a-3edd-43d8-95e8-91721b38c1c1).|  
|Оператор Spread|[Оператор spread](http://msdn.microsoft.com/Library/10263a4c-bd27-4d87-9917-fb4b6bf373db) (`…`) расширяет доступные для итерации выражения в отдельные аргументы. Например, `a.b(…array)` примерно равен `a.b.apply(a, array)`.|  
|Символы|Объекты [Symbol](http://msdn.microsoft.com/Library/2ad059f1-4b7f-4758-882a-c74ce1283ab0) позволяют добавлять свойства в существующие объекты без создания помех существующим свойствам объектов, непредусмотренной видимости и других несогласованных дополнений, которые могут быть реализованы другими частями кода.|  
|Строки шаблона|[Строки шаблона](http://msdn.microsoft.com/Library/f2e525a5-b0fc-49c3-95a0-641788e5c12a) — это строковые литералы, позволяющие оценивать выражения и сцеплять их со строковым литералом.|  
|Усовершенствования Юникода|Была усовершенствована поддержка Юникода. Так, новый формат escape-последовательности поддерживает астральные кодовые точки (кодовые точки с более 4 шестнадцатеричных цифр). См. дополнительные сведения о [специальных символах](http://msdn.microsoft.com/Library/3b38b1bd-1f0f-4748-b13e-55cab36fd126).|  
|Множество WeakSet|Множество [WeakSet](http://msdn.microsoft.com/Library/f97e6e7c-d678-4e32-978e-d949a7cafa3a) — это коллекция объектов, которая будет удалена как мусор при отсутствии доступных ссылок на нее.|
