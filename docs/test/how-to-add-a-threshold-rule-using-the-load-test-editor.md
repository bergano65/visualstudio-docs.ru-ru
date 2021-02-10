---
title: Добавление правила порога для нагрузочного тестирования
description: Сведения о правилах пороговых значений в нагрузочных тестах, которые сравнивают значение счетчика производительности со значением константы или другого счетчика производительности.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: aa8e9af0c4ca25b29e0194e5515250ceb4cd6254
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908644"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Практическое руководство. Добавление правила порога с помощью редактора тестовой нагрузки

Правила порогов в нагрузочных тестах сравнивают значение счетчика производительности со значением константы или другого счетчика производительности.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Чтобы добавить правило порога

1. Откройте нагрузочный тест.

2. В редакторе тестовой нагрузки разверните узел **Наборы счетчиков**.

3. Разверните одну из **категорий счетчиков** в одном из наборов счетчиков. Например, можно выбрать **LoadTest:Scenario**. Разверните узел.

4. В разделе **LoadTest:Scenario** щелкните правой кнопкой мыши один из счетчиков, например **Нагрузка пользователей**. Выберите команду **Добавить правило порога**.

     Откроется диалоговое окно **Добавление правила порога**.

5. Можно выбрать один из двух типов правил: **сравнивать с константой** или **сравнивать счетчики**. Выберите нужный тип и установите значения.

    > [!NOTE]
    > Чтобы нарушением считалось превышение порогового значения, установите для свойства **Оповещать при превышении** значение **True**, а чтобы нарушением считалось получение показания ниже порогового значения, установите значение **False**.

## <a name="see-also"></a>См. также раздел

- [Анализ нарушений правил порогов](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Указание наборов счетчиков и правил порогов для компьютеров в нагрузочном тесте](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Анализ результатов нагрузочных тестов](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
