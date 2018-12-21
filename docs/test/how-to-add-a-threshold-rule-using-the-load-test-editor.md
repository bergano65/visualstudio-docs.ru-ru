---
title: Добавление правила порога для нагрузочного тестирования
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ac4b542c7f9b557ad04ead05422f8c89cd4f909c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063374"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Как выполнить Добавление правила порога с помощью редактора тестовой нагрузки

Правила порогов в нагрузочных тестах сравнивают значение счетчика производительности со значением константы или другого счетчика производительности.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Чтобы добавить правило порога

1.  Откройте нагрузочный тест.

2.  В редакторе тестовой нагрузки разверните узел **Наборы счетчиков**.

3.  Разверните одну из **категорий счетчиков** в одном из наборов счетчиков. Например, можно выбрать **LoadTest:Scenario**. Разверните узел.

4.  В разделе **LoadTest:Scenario** щелкните правой кнопкой мыши один из счетчиков, например **Нагрузка пользователей**. Выберите команду **Добавить правило порога**.

     Откроется диалоговое окно **Добавление правила порога**.

5.  Можно выбрать один из двух типов правил: **Сравнить с константой** и **Сравнить со счетчиком**. Выберите нужный тип и установите значения.

    > [!NOTE]
    > Чтобы нарушением считалось превышение порогового значения, установите для свойства **Оповещать при превышении** значение **True**, а чтобы нарушением считалось получение показания ниже порогового значения, установите значение **False**.

## <a name="see-also"></a>См. также

- [Анализ нарушений правил порогов](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Указание наборов счетчиков и правил порогов для компьютеров в нагрузочном тесте](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Анализ результатов нагрузочных тестов](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
