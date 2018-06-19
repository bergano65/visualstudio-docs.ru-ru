---
title: Устранение неполадок скриптов (JavaScript) | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- automative type conversion
- troubleshooting scripts
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e0193e6dc0996d5e2d0d3df7103c7705d29477
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569284"
---
# <a name="troubleshooting-your-scripts-javascript"></a>Устранение неполадок скриптов (JavaScript)
Любой язык программирования несет в себе некоторую долю неожиданности. Например, значение `null` в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] работает не так, как значение `Null` в C или C++.  
  
 Ниже приведены некоторые проблемы, с которыми вы можете столкнуться при написании скриптов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax-errors"></a>Синтаксические ошибки  
 При создании скриптов очень важно внимание к деталям. Например, строки должны заключаться в кавычки.  
  
## <a name="order-of-script-interpretation"></a>Порядок интерпретации скриптов  
 Интерпретация [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] является частью процесса синтаксического анализа HTML в веб-браузере. Если поместить скрипт внутрь тега \<HEAD> в документе, он будет интерпретироваться раньше любой части тега \<BODY>. Если у вас есть объекты, создаваемые в теге \<BODY>, то при анализе \<HEAD> они еще не существуют и поэтому не могут использоваться скриптом.  
  
> [!NOTE]
>  Такое поведение характерно для Internet Explorer. ASP и WSH имеют различные модели выполнения (как и другие узлы).  
  
## <a name="automatic-type-coercion"></a>Автоматическое приведение типов  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] — это слабо типизированный язык с автоматическим приведением. Хотя значения, имеющие разные типы, не равны, в следующем примере выражения дают значение **true**.  
  
```JavaScript  
"100" == 100;  
false == 0;  
```  
  
 Чтобы проверить совпадение по типу и значению, используйте оператор строгого равенства (===). Оба следующих выражения дают значение false:  
  
```JavaScript  
"100" === 100;  
false === 0;  
```  
  
## <a name="operator-precedence"></a>Приоритет операторов  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md) определяет, когда выполняется операция во время вычисления выражения. В следующем примере умножение выполняется до вычитания, хотя последнее и стоит на первом месте.  
  
```JavaScript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## <a name="using-forin-loops-with-objects"></a>Использование циклов "for...in" с объектами  
 При итерации по свойствам объекта с помощью цикла [for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) вы не можете предсказать порядок, в котором поля объекта назначаются переменной счетчика циклов, или управлять им. Кроме того, этот порядок может отличаться в разных реализациях языка.  
  
## <a name="with-keyword"></a>Ключевое слово with  
 Оператор [with](../../javascript/reference/with-statement-javascript.md) удобно применять для доступа к свойствам, которые уже существуют в указанном объекте, но не могут использоваться для добавления свойств в объект. Чтобы создать свойства в объекте, нужно сослаться на него.  
  
## <a name="this-keyword"></a>Ключевое слово this  
 Хотя вы используете ключевое слово `this` внутри определения объекта, чтобы сослаться на сам объект, вы не можете использовать `this` или аналогичные ключевые слова для ссылки на выполняющуюся в данный функцию, если она не является определением объекта. Если функция должна быть назначена объекту в качестве метода, в можете использовать ключевое слово `this` в рамках этой функции для ссылки на объект.  
  
## <a name="writing-a-script-that-writes-a-script-in-internet-explorer"></a>Создание скрипта, который пишет скрипт в Internet Explorer  
 Тег \</SCRIPT > завершает текущий скрипт, если его встречает интерпретатор. Чтобы отобразить сам "\</SCRIPT>", перепишите его в виде по меньшей мере двух строк, например "\</SCR" и "IPT>", которые затем можно сцепить друг с другом в оператор, который их выводит.  
  
## <a name="implicit-window-references-in-internet-explorer"></a>Неявные ссылки на окна в Internet Explorer  
 Так как одновременно можно открыть несколько окон, любая неявная ссылка на окно указывает на текущее окно. Для других окон нужно использовать явную ссылку.