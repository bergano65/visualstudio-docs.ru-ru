---
title: 'Как: печать схем из представления графика и представления модели содержимого | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 7e1785e4-4aaf-4c66-8735-51e7ca035565
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86f36e09e691acd0a94a27f1cc7d4b510e2b1dbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-print-diagrams-from-the-graph-view-and-the-content-model-view"></a>Как печатать схемы из представления графика и представления модели содержимого
Данный раздел описывает процесс печати схемы из представления графика или представления модели содержимого.  
  
### <a name="to-print-diagrams-from-the-xml-schema-designer"></a>Печать схем из конструктора XML-схем  
  
1.  Откройте файл XSD в Visual Studio и добавьте несколько узлов [рабочей области конструктора схем XML](../xml-tools/xml-schema-designer-workspace.md).  
  
2.  Экспортируйте диаграмму в XPS-файл с помощью **экспортировать схему как рисунок...**  пункта контекстного меню в области конструктора представления графика или представлении модели содержимого.  
  
     При экспорте схемы из представления графика в XPS-файл будет экспортирована вся область конструктора. При экспорте схемы из представления модели содержимого, когда область конструктора представления модели содержимого содержит более одного узла, в XPS-файл будет экспортирован только первый узел.  
  
3.  Распечатайте сохраненный в XPS-файле образ с использованием средства просмотра XPS.  
  
## <a name="see-also"></a>См. также  
 [Представление графика](../xml-tools/graph-view.md)   
 [Представление модели содержимого](../xml-tools/content-model-view.md)   
 [Рабочая область конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md)