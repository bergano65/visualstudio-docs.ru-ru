---
title: 'Практическое: Оценка выражения XPath | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 05758034c0228f0efd7fb3ae63bd3b7e0d5e3095
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210435"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Практическое руководство. Оценка выражения XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно оценить выражения XPath **"Быстрая проверка"** диалоговое окно. Выражение XPath должно быть допустимым и соответствовать рекомендация W3C языка XPath версии 1.0. Текущий контекст XSLT — то есть `self::node()` узел в **"Локальные"** окно — предоставляет контекст оценки для выражения XPath.  
  
 В следующем списке перечислены функции, которые поддерживаются при оценке выражения XPath.  
  
-   Поддерживаются встроенные функции XPath.  
  
-   Не поддерживаются встроенные функции XSLT.  
  
-   Не поддерживаются определяемые пользователем функции.  
  
> [!NOTE]
>  В следующей процедуре используются файлы Avg.XSL и books.xml из [Пошаговое руководство: отладка таблицы стилей XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) раздела.  
  
### <a name="to-evaluate-an-xpath-expression"></a>Оценка выражения XPath  
  
1.  Добавьте точку останова в начальный тег `xsl:if`.  
  
2.  Нажмите кнопку **Отладка XSL** кнопки на панели инструментов редактора XML.  
  
     Отладчик начинается и останавлявается на теге `xsl:if`.  
  
3.  Щелкните правой кнопкой мыши и выберите **"Быстрая проверка"**.  
  
     **"Быстрая проверка"** диалоговое окно.  
  
4.  Введите `./price/text()` в **выражение** поле **"Быстрая проверка"** диалоговое окно и нажмите кнопку **пересчитать**.  
  
     Цены на текущий узел книги отображается в **значение** поле.  
  
5.  Измените выражение XPath `./price/text() < $bookAverage` и нажмите кнопку **пересчитать**.  
  
     **Значение** поле показывает, что возвращает выражение XPath `true`.  
  
## <a name="see-also"></a>См. также  
 [Отладка XSLT](../xml-tools/debugging-xslt.md)

