---
title: Пример расширения Excel. Класс ActionFilter | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c286f25159f3ee1934a27d2242e97482f7ec424
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672181"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Пример расширения Excel. Класс ActionFilter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Этот внутренний класс расширяет класс [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) и представляет фильтр для действий теста в элементе [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

## <a name="simple-properties"></a>Простые свойства
 Эти свойства только для чтения позволяют разработчику указывать, как фильтр действий теста должен применяться платформой закодированных тестов пользовательского интерфейса. Например, свойство `UITestActionFilter.Name` предоставляет имя фильтра действий. Другие свойства получают категорию (`UITestActionFilter.Category`) фильтра действий, тип фильтра (`UITestActionFilter.FilterType`), имя группы (`UITestActionFilter.Group`) для действий теста, фильтруемых данным фильтром действий. Другие свойства определяют, следует ли применять время ожидания (`UITestActionFilter.ApplyTimeout`), а также включен ли фильтр действий теста (`UITestActionFilter.Enabled`).

## <a name="processrule-method"></a>Метод ProcessRule
 Этот метод вызывается средой обработки закодированных тестов пользовательского интерфейса; он выполняет фильтр для предоставленного объекта `IUITestActionStack`. Данное переопределение удаляет действие щелчка мыши в ячейке, если следующее действие в стеке отправляет нажатия клавиш клавиатуры в этой ячейке. Затем оно возвращает значение `false`.

## <a name="private-methods"></a>Закрытые методы
 Метод `IsLeftClick` определяет, представляет ли указанное действие щелчок левой кнопкой мыши. Метод `AreActionsOnSameExcelCell` определяет, выполняются ли два указанных действия в одной ячейке Excel.

## <a name="see-also"></a>См. также

- [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
