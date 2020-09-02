---
title: Схема XML. Печать схем из представлений графика и модели содержимого
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 7e1785e4-4aaf-4c66-8735-51e7ca035565
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5aef4b2a7bc040a75a97bc66f26526053f4cada
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817129"
---
# <a name="how-to-print-diagrams-from-the-graph-view-and-the-content-model-view"></a>Практическое руководство. Печать схем из представления графика и представления модели содержимого

В этой статье описана печать схемы из представления графика или представления модели содержимого в конструкторе схем XML.

## <a name="to-print-diagrams-from-the-xml-schema-designer"></a>Печать схем из конструктора XML-схем

1. Откройте XSD-файл в Visual Studio и добавьте несколько узлов в [рабочую область конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md).

2. Экспортируйте диаграмму в XPS-файл с использованием пункта контекстного меню **Экспортировать схему в виде изображения** (щелчок правой кнопкой) области конструктора в представлении графика или представлении модели содержимого.

     При экспорте схемы из представления графика в XPS-файл экспортируется вся область конструктора. При экспорте схемы из представления модели содержимого, когда область конструктора представления модели содержимого содержит более одного узла, в XPS-файл экспортируется только первый узел.

3. Распечатайте сохраненный в XPS-файле образ с использованием средства просмотра XPS.

## <a name="see-also"></a>См. также

- [Представление диаграммы](../xml-tools/graph-view.md)
- [Представление модели содержимого](../xml-tools/content-model-view.md)
- [Рабочая область конструктора схем XML](../xml-tools/xml-schema-designer-workspace.md)
