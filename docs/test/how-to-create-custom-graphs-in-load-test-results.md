---
title: Как выполнить Создание пользовательских графиков в результатах нагрузочного теста
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, creating
- load test results graphs
ms.assetid: 17fcafce-76f9-4411-9389-6e5376eab236
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: 8fd80a4d7cbfeb7cf79ae3dddad9aa1da367fd87
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992780"
---
# <a name="how-to-create-custom-graphs-in-load-test-results"></a>Как выполнить Создание пользовательских графиков в результатах нагрузочного теста

Можно разработать диаграммы, отображающие определенные сведения о результатах нагрузочных тестов. При создании диаграммы следует указать счетчики нагрузочных тестов, которые будут на ней представлены.

Выполнение следующих процедур осуществляется либо в ходе нагрузочного теста, либо по его завершении.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-load-test-results-graph"></a>Создание настраиваемой диаграммы результатов нагрузочного теста

1.  На панели инструментов **нагрузочных тестов** нажмите кнопку **Добавить новую диаграмму**.

     \- или -

     В **анализаторе тестовой нагрузки** щелкните правой кнопкой мыши на панели **Счетчики** или в диаграмме и выберите команду **Добавить диаграмму**.

     Откроется диалоговое окно **Ввод имени диаграммы**.

2.  В поле **Имя диаграммы** введите имя диаграммы и нажмите кнопку **ОК**.

     В **анализаторе тестовой нагрузки** появится новая диаграмма. Она появится в выбранной в настоящий момент области диаграммы и заменит ранее отображавшуюся диаграмму.

3.  Настройте новую диаграмму, добавив в нее счетчики. Дополнительные сведения см. в разделе [Как добавлять и удалять счетчики на графах](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

## <a name="see-also"></a>См. также

- [Анализ результатов нагрузочного тестирования в представлении диаграмм](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Практическое руководство. Добавление и удаление счетчиков на графах](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)