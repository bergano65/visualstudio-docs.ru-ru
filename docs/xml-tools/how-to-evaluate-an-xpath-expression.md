---
title: Вычисление выражения XPath во время отладки
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2e0b6c84fa9447dc38aa7976fa59bb5aa67d5c3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592728"
---
# <a name="evaluate-xpath-expressions"></a>Вычисление выражений XPath

Выражения XPath можно вычислить с помощью окна **Быстрая проверка** во время отладки. Выражение XPath должно быть допустимым и соответствовать рекомендация W3C языка XPath версии 1.0. Текущий контекст XSLT (т. е. узел `self::node()` в окне **локальные** ) предоставляет контекст вычисления для выражения XPath.

При вычислении выражения XPath:

- Поддерживаются встроенные функции XPath.

- Встроенные функции XSLT и определяемые пользователем функции не поддерживаются.

> [!NOTE]
> Отладка XSLT доступна только в выпуске Visual Studio Enterprise Edition.

## <a name="evaluate-an-xpath-expression"></a>Вычисление выражения XPath

В следующей процедуре используются файлы *Белов-авераже. xsl* и *Books. XML* из [пошагового руководства: Отладка страницы таблицы стилей XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) .

1. Добавьте точку останова в начальный тег `xsl:if`.

2. Чтобы начать отладку, выберите **XML** > **начать отладку XSLT** в строке меню (или нажмите клавиши **ALT**+**F5**).

   Отладчик начинается и останавлявается на теге `xsl:if`.

3. Щелкните правой кнопкой мыши и выберите **Быстрая проверка**.

   Откроется окно **Быстрая проверка** .

4. Введите `./price/text()` в поле **выражение** диалогового окна **Быстрая проверка** , а затем нажмите кнопку Повторное **Вычисление**.

   Цена текущего узла книги отображается в поле **значение** .

   ![Вычисление выражения XPath в окне "Быстрая проверка"](media/quickwatch-price.png)

5. Измените выражение XPath на `./price/text() < $bookAverage` и нажмите кнопку Повторное **Вычисление**.

   В поле **значение** показано, что выражение XPath принимает значение `true`.

## <a name="see-also"></a>См. также:

- [Отладка XSLT](../xml-tools/debugging-xslt.md)
