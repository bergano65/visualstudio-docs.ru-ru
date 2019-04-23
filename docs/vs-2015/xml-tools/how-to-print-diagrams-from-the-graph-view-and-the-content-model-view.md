---
title: Практическое руководство. Печать схем из представления графика и представления модели содержимого | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 7e1785e4-4aaf-4c66-8735-51e7ca035565
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cae78a5f32037111a870058f92ea0d0f36f23f56
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60088721"
---
# <a name="how-to-print-diagrams-from-the-graph-view-and-the-content-model-view"></a>Практическое руководство. Печать схем из представления графика и представления модели содержимого
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Данный раздел описывает процесс печати схемы из представления графика или представления модели содержимого.  
  
### <a name="to-print-diagrams-from-the-xml-schema-designer"></a>Печать схем из конструктора XML-схем  
  
1. Откройте XSD-файл в Visual Studio и добавьте несколько узлов [рабочей области конструктора схем XML](../xml-tools/xml-schema-designer-workspace.md).  
  
2. Экспортируйте диаграмму в XPS-файлы с помощью **экспортировать схему как рисунок …** пункт контекстного меню в области конструктора представления графика или представления модели содержимого.  
  
     При экспорте схемы из представления графика в XPS-файл будет экспортирована вся область конструктора. При экспорте схемы из представления модели содержимого, когда область конструктора представления модели содержимого содержит более одного узла, в XPS-файл будет экспортирован только первый узел.  
  
3. Распечатайте сохраненный в XPS-файле образ с использованием средства просмотра XPS.  
  
## <a name="see-also"></a>См. также  
 [Представление графика](../xml-tools/graph-view.md)   
 [Представление модели содержимого](../xml-tools/content-model-view.md)   
 [Рабочая область конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md)
