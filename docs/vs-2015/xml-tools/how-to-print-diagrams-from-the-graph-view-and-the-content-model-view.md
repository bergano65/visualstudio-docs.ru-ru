---
title: 'Практическое: печать схем из представления графика и представления модели содержимого | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e1785e4-4aaf-4c66-8735-51e7ca035565
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 53774a410a05244f4b005fac1b14fe5776794a68
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305478"
---
# <a name="how-to-print-diagrams-from-the-graph-view-and-the-content-model-view"></a>Как печатать схемы из представления графика и представления модели содержимого
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Данный раздел описывает процесс печати схемы из представления графика или представления модели содержимого.  
  
### <a name="to-print-diagrams-from-the-xml-schema-designer"></a>Печать схем из конструктора XML-схем  
  
1.  Откройте XSD-файл в Visual Studio и добавьте несколько узлов [рабочей области конструктора схем XML](../xml-tools/xml-schema-designer-workspace.md).  
  
2.  Экспортируйте диаграмму в XPS-файлы с помощью **экспортировать схему как рисунок …** пункт контекстного меню в области конструктора представления графика или представления модели содержимого.  
  
     При экспорте схемы из представления графика в XPS-файл будет экспортирована вся область конструктора. При экспорте схемы из представления модели содержимого, когда область конструктора представления модели содержимого содержит более одного узла, в XPS-файл будет экспортирован только первый узел.  
  
3.  Распечатайте сохраненный в XPS-файле образ с использованием средства просмотра XPS.  
  
## <a name="see-also"></a>См. также  
 [Представление графика](../xml-tools/graph-view.md)   
 [Представление модели содержимого](../xml-tools/content-model-view.md)   
 [Рабочая область конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md)



