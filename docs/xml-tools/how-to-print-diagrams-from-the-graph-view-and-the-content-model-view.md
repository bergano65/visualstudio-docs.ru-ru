---
title: Печать схем из представления графика и представления модели содержимого конструктора схемы XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 7e1785e4-4aaf-4c66-8735-51e7ca035565
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd147b5a7b491c17e0ed0024cfe471762e6160b1
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269713"
---
# <a name="how-to-print-diagrams-from-the-graph-view-and-the-content-model-view"></a>Как выполнить Печать схем из представления графика и представления модели содержимого

В этом разделе описывается печати схемы из представления графика или содержимого модели представления из конструктора схем XML.

## <a name="to-print-diagrams-from-the-xml-schema-designer"></a>Печать схем из конструктора XML-схем

1.  Откройте XSD-файл в Visual Studio и добавьте несколько узлов [рабочей области конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md).

2.  Экспортируйте диаграмму в XPS-файлы с помощью **экспортировать схему как рисунок** (правой кнопкой мыши) контекстного меню в области конструктора представления графика или представления модели содержимого.

     При экспорте схемы из представления графика, вся область конструктора экспортируется в XPS-файл. При экспорте схемы из представления модели содержимого и более одного узла отображается в рабочей области конструктора представления модели содержимого, в XPS-файл экспортируется только первый узел.

3.  Распечатайте сохраненный в XPS-файле образ с использованием средства просмотра XPS.

## <a name="see-also"></a>См. также

- [Представление диаграммы](../xml-tools/graph-view.md)
- [Представление модели содержимого](../xml-tools/content-model-view.md)
- [Рабочая область конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md)