---
title: Оценка выражения XPath во время отладки
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1585b54d084e3471583f9388d63f5c17e65fc3a7
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526326"
---
# <a name="evaluate-xpath-expressions"></a>Вычисление выражения XPath

Можно вычислять выражения XPath с помощью **"Быстрая проверка"** окна во время отладки. Выражение XPath должно быть допустимым и соответствовать рекомендация W3C языка XPath версии 1.0. Текущий контекст XSLT (то есть `self::node()` узел в **"Локальные"** окно) предоставляет контекст оценки для выражения XPath.

При вычислении выражения XPath:

- Поддерживаются встроенные функции XPath.

- Встроенные функции XSLT и определяемые пользователем функции не поддерживаются.

> [!NOTE]
> Отладка XSLT доступна только в выпуске Visual Studio Enterprise.

## <a name="evaluate-an-xpath-expression"></a>Оценка выражения XPath

В следующей процедуре используется *ниже average.xsl* и *books.xml* файлов из [Пошаговое руководство: Отладка таблицы стилей XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) страницы.

1. Добавьте точку останова в начальный тег `xsl:if`.

2. Чтобы начать отладку, выберите **XML** > **начать отладку XSLT** в строке меню (или нажмите клавишу **Alt**+**F5** ).

   Отладчик начинается и останавлявается на теге `xsl:if`.

3. Щелкните правой кнопкой мыши и выберите **"Быстрая проверка"**.

   **"Быстрая проверка"** откроется окно.

4. Введите `./price/text()` в **выражение** поле **"Быстрая проверка"** диалоговое окно, а затем кнопку **пересчитать**.

   Цены на текущий узел книги отображается в **значение** поле.

   ![Оценка выражения XPath в окне "Быстрая проверка"](media/quickwatch-price.png)

5. Измените выражение XPath `./price/text() < $bookAverage` и нажмите кнопку **пересчитать**.

   **Значение** поле показывает, что возвращает выражение XPath `true`.

## <a name="see-also"></a>См. также

- [Отладка XSLT](../xml-tools/debugging-xslt.md)