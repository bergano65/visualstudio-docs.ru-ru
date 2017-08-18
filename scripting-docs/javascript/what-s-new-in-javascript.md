---
title: "Новые возможности JavaScript | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 342b68ef-df93-48c4-81de-bdf6b6ce58d9
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 540d10958a7f2d406a6d70a633fc09a2cada8f41
ms.contentlocale: ru-ru
ms.lasthandoff: 08/11/2017

---
# <a name="what39s-new-in-javascript"></a>Новые возможности JavaScript
В этом документе рассматриваются новые функции JavaScript, поддерживаемые в [режиме Edge](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx), [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)], а также приложениями Магазина Windows Phone.  
  
 Сведения об элементах JavaScript, которые поддерживаются в режиме границ, но не рекомендованы к использованию в приложениях [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)], см. в разделе [Сведения о версии](../javascript/reference/javascript-version-information.md).  
  
> [!IMPORTANT]
>  Сведения о создании приложений [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] и приложений Магазина Windows Phone с помощью JavaScript, включая сведения о редакторе JavaScript Visual Studio и других компонентах, см. в статье [Разработка приложений Магазина Windows с помощью Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkID=238263).  
  
## <a name="new-features-in-javascript"></a>Новые возможности в JavaScript  
  
|Функция|Описание|  
|-------------|-----------------|  
|Классы|Новый синтаксис поддерживает объявление [классов](../javascript/reference/class-statement-javascript.md).|  
|Обещания|[Обещания](../javascript/reference/promise-object-javascript.md) упрощают создание асинхронного и более чистого кода. Конструкторы обещаний поддерживаются вместе со служебными методами `all` и `race`.|  
|Итераторы|Теперь можно выполнить итерацию поддерживающих итерацию объектов (включая массивы, объекты, похожие на массивы, и итераторы), вызывая пользовательский обработчик итераций с операторами, которые должны быть исполнены для значения каждого свойства по отдельности. См. дополнительные сведения см. об [итераторах и генераторах](../javascript/advanced/iterators-and-generators-javascript.md). **Примечание.** Генераторы пока не поддерживаются.|  
|Функции со стрелкой|Функция со стрелкой (=>) предоставляет сокращенный синтаксис для ключевого слова `function` с лексической привязкой `this`.|  
|Новые методы для встроенных объектов|Встроенные объекты [Array Object](../javascript/reference/array-object-javascript.md), [Math Object](../javascript/reference/math-object-javascript.md), [Number Object](../javascript/reference/number-object-javascript.md), [Object Object](../javascript/reference/object-object-javascript.md) и [String Object](../javascript/reference/string-object-javascript.md) предоставляют множество новых служебных функций и свойств для обработки и инспектирования данных.|  
|Усовершенствования объектного литерала|Объекты теперь поддерживают вычисляемые свойства, точные определения методов и сокращенный синтаксис для свойств, значения которых инициализируются в переменную с таким же именем. См. дополнительные сведения о [создании объектов](../javascript/creating-objects-javascript.md).|  
|Прокси-элементы|[Прокси-элементы](../javascript/reference/proxy-object-javascript.md) позволяют настраивать пользовательское поведение объектов.|  
|Параметры Rest|Параметры Rest позволяют преобразовать последовательные аргументы в вызове функции в массив. См. дополнительные сведения о [функциях](../javascript/functions-javascript.md).|  
|Оператор Spread|[Оператор spread](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md) (`...`) расширяет доступные для итерации выражения в отдельные аргументы. Например, `a.b(...array)` примерно равен `a.b.apply(a, array)`.|  
|Символы|Объекты [Symbol](../javascript/reference/symbol-object-javascript.md) позволяют добавлять свойства в существующие объекты без создания помех существующим свойствам объектов, непредусмотренной видимости и других несогласованных дополнений, которые могут быть реализованы другими частями кода.|  
|Строки шаблона|[Строки шаблона](../javascript/advanced/template-strings-javascript.md) — это строковые литералы, позволяющие оценивать выражения и сцеплять их со строковым литералом.|  
|Усовершенствования Юникода|Была усовершенствована поддержка Юникода. Так, новый формат escape-последовательности поддерживает астральные кодовые точки (кодовые точки с более 4 шестнадцатеричных цифр). См. дополнительные сведения о [специальных символах](../javascript/advanced/special-characters-javascript.md).|  
|Множество WeakSet|Множество [WeakSet](../javascript/reference/weakset-object-javascript.md) — это коллекция объектов, которая будет удалена как мусор при отсутствии доступных ссылок на нее.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку JavaScript](../javascript/javascript-language-reference.md)
