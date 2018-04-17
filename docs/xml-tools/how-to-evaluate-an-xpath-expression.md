---
title: 'Как: Оценка выражения XPath | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c026e9d2005156189afc9dd478c75397a997d8f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Практическое руководство. Оценка выражения XPath
Можно оценить выражения XPath с **Быстрая проверка** диалоговое окно. Выражение XPath должно быть допустимым и соответствовать рекомендация W3C языка XPath версии 1.0. Текущий контекст XSLT — то есть `self::node()` узел в **локальные** окно — предоставляет контекст оценки выражения XPath.  
  
 В следующем списке перечислены функции, которые поддерживаются при оценке выражения XPath.  
  
-   Поддерживаются встроенные функции XPath.  
  
-   Не поддерживаются встроенные функции XSLT.  
  
-   Не поддерживаются определяемые пользователем функции.  
  
> [!NOTE]
>  В следующей процедуре используются файлы belowAvg.xsl и books.xml [Пошаговое руководство: отладка таблицы стилей XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) раздела.  
  
### <a name="to-evaluate-an-xpath-expression"></a>Оценка выражения XPath  
  
1.  Добавьте точку останова в начальный тег `xsl:if`.  
  
2.  Нажмите кнопку **Отладка XSL** на панели инструментов редактора XML.  
  
     Отладчик начинается и останавлявается на теге `xsl:if`.  
  
3.  Щелкните правой кнопкой мыши и выберите **Быстрая проверка**.  
  
     **Быстрая проверка** диалоговое окно.  
  
4.  Введите `./price/text()` в **выражение** поле **Быстрая проверка** диалоговое окно и нажмите кнопку **пересчитать**.  
  
     Цены на текущий узел книги отображается в **значение** поле.  
  
5.  Измените выражение XPath для `./price/text() < $bookAverage` и нажмите кнопку **пересчитать**.  
  
     **Значение** показывает, что оценка выражения XPath дает значение `true`.  
  
## <a name="see-also"></a>См. также  
 [Отладка XSLT](../xml-tools/debugging-xslt.md)