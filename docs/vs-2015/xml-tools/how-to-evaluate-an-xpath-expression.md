---
title: Как вычислить выражение XPath | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ecec9004506a9bd05d3d773e44bb264af363f96f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670869"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Практическое руководство. Оценка выражения XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Выражения XPath можно вычислить с помощью диалогового окна **Быстрая проверка** . Выражение XPath должно быть допустимым и соответствовать рекомендация W3C языка XPath версии 1.0. Текущий контекст XSLT, т. е. `self::node()` узел в окне **локальные** , предоставляет контекст оценки для выражения XPath.

 В следующем списке перечислены функции, которые поддерживаются при оценке выражения XPath.

- Поддерживаются встроенные функции XPath.

- Не поддерживаются встроенные функции XSLT.

- Не поддерживаются определяемые пользователем функции.

> [!NOTE]
> В следующей процедуре используются файлы Беловавг. XSL и books.xml из раздела [Пошаговое руководство: Отладка таблицы стилей XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) .

### <a name="to-evaluate-an-xpath-expression"></a>Оценка выражения XPath

1. Добавьте точку останова в начальный тег `xsl:if`.

2. Нажмите кнопку **Отладка XSL** на панели инструментов редактора XML.

     Отладчик начинается и останавлявается на теге `xsl:if`.

3. Щелкните правой кнопкой мыши и выберите пункт **Быстрая проверка**.

     Откроется диалоговое окно **Быстрая проверка** .

4. Введите `./price/text()` в поле **выражение** диалогового окна **Быстрая проверка** и нажмите кнопку Повторное **Вычисление**.

     В поле **Значение** появится цена для текущего узла книги.

5. Измените выражение XPath на `./price/text() < $bookAverage` и нажмите кнопку **Пересчитать**.

     В поле **Значение** будет показано, что оценка выражения XPath дает значение `true`.

## <a name="see-also"></a>См. также:
 [Отладка XSLT](../xml-tools/debugging-xslt.md)
