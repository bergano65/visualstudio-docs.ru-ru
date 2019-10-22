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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670869"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Практическое руководство. Оценка выражения XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Выражения XPath можно вычислить с помощью диалогового окна **Быстрая проверка** . Выражение XPath должно быть допустимым и соответствовать рекомендация W3C языка XPath версии 1.0. Текущий контекст XSLT, т. е. узел `self::node()` в окне **локальные** , предоставляет контекст оценки для выражения XPath.

 В следующем списке перечислены функции, которые поддерживаются при оценке выражения XPath.

- Поддерживаются встроенные функции XPath.

- Не поддерживаются встроенные функции XSLT.

- Не поддерживаются определяемые пользователем функции.

> [!NOTE]
> В следующей процедуре используются файлы Беловавг. XSL и Books. XML из раздела [Пошаговое руководство: Отладка таблицы стилей XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) .

### <a name="to-evaluate-an-xpath-expression"></a>Оценка выражения XPath

1. Добавьте точку останова в начальный тег `xsl:if`.

2. Нажмите кнопку **Отладка XSL** на панели инструментов редактора XML.

     Отладчик начинается и останавлявается на теге `xsl:if`.

3. Щелкните правой кнопкой мыши и выберите **Быстрая проверка**.

     Откроется диалоговое окно **Быстрая проверка** .

4. Введите `./price/text()` в поле **выражение** диалогового окна **Быстрая проверка** и нажмите кнопку Повторное **Вычисление**.

     Цена текущего узла книги отображается в поле **значение** .

5. Измените выражение XPath на `./price/text() < $bookAverage` и нажмите кнопку Повторное **Вычисление**.

     В поле **значение** показано, что выражение XPath принимает значение `true`.

## <a name="see-also"></a>См. также раздел
 [Отладка XSLT](../xml-tools/debugging-xslt.md)
