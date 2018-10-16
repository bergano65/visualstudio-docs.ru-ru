---
title: Печать схем из представления графика и представления модели содержимого конструктора схемы XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 7e1785e4-4aaf-4c66-8735-51e7ca035565
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dcb65958f7b339338b99495646bab57bd77af054
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548236"
---
# <a name="how-to-print-diagrams-from-the-graph-view-and-the-content-model-view"></a>Как: печать схем из представления графика и представления модели содержимого

В этом разделе описывается печати схемы из представления графика или содержимого модели представления из конструкторе схемы XML.

## <a name="to-print-diagrams-from-the-xml-schema-designer"></a>Печать схем из конструктора XML-схем

1.  Откройте файл XSD в Visual Studio и добавьте несколько узлов [рабочей области конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md).

2.  Экспортируйте диаграмму в XPS-файл с помощью **экспортировать схему как рисунок** пункта контекстного меню в области конструктора представления графика или представлении модели содержимого.

     При экспорте схемы из представления графика, экспортируется вся область конструктора в XPS-файл. При экспорте схемы из представления модели содержимого и более чем один узел отображается в рабочей области конструктора представления модели содержимого, экспортируется только первый узел в XPS-файл.

3.  Распечатайте сохраненный в XPS-файле образ с использованием средства просмотра XPS.

## <a name="see-also"></a>См. также

- [Представление диаграммы](../xml-tools/graph-view.md)
- [Представление модели содержимого](../xml-tools/content-model-view.md)
- [Рабочая область конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md)