---
title: Практическое руководство. Оценка выражения XPath | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a0c79da47b83f8bf5b44af16ca291e2424011b80
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075614"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Практическое руководство. вычислить выражение XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно оценить выражения XPath **"Быстрая проверка"** диалоговое окно. Выражение XPath должно быть допустимым и соответствовать рекомендация W3C языка XPath версии 1.0. Текущий контекст XSLT — то есть `self::node()` узел в **"Локальные"** окно — предоставляет контекст оценки для выражения XPath.  
  
 В следующем списке перечислены функции, которые поддерживаются при оценке выражения XPath.  
  
- Поддерживаются встроенные функции XPath.  
  
- Не поддерживаются встроенные функции XSLT.  
  
- Не поддерживаются определяемые пользователем функции.  
  
> [!NOTE]
>  В следующей процедуре используются файлы Avg.XSL и books.xml из [Пошаговое руководство: Отладка таблицы стилей XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) раздела.  
  
### <a name="to-evaluate-an-xpath-expression"></a>Оценка выражения XPath  
  
1. Добавьте точку останова в начальный тег `xsl:if`.  
  
2. Нажмите кнопку **Отладка XSL** кнопки на панели инструментов редактора XML.  
  
     Отладчик начинается и останавлявается на теге `xsl:if`.  
  
3. Щелкните правой кнопкой мыши и выберите **"Быстрая проверка"**.  
  
     **"Быстрая проверка"** диалоговое окно.  
  
4. Введите `./price/text()` в **выражение** поле **"Быстрая проверка"** диалоговое окно и нажмите кнопку **пересчитать**.  
  
     Цены на текущий узел книги отображается в **значение** поле.  
  
5. Измените выражение XPath `./price/text() < $bookAverage` и нажмите кнопку **пересчитать**.  
  
     **Значение** поле показывает, что возвращает выражение XPath `true`.  
  
## <a name="see-also"></a>См. также  
 [Отладка XSLT](../xml-tools/debugging-xslt.md)
