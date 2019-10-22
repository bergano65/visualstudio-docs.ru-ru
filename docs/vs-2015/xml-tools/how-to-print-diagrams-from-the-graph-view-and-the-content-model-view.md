---
title: Как печатать диаграммы из представления графика и представления модели содержимого | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 7e1785e4-4aaf-4c66-8735-51e7ca035565
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: de59aac6bc40e58b6da9b71fd0cc81d432fe41bd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670843"
---
# <a name="how-to-print-diagrams-from-the-graph-view-and-the-content-model-view"></a>Как печатать схемы из представления графика и представления модели содержимого
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Данный раздел описывает процесс печати схемы из представления графика или представления модели содержимого.

### <a name="to-print-diagrams-from-the-xml-schema-designer"></a>Печать схем из конструктора XML-схем

1. Откройте XSD-файл в Visual Studio и добавьте некоторые узлы в [рабочую область конструктор схем XML](../xml-tools/xml-schema-designer-workspace.md).

2. Экспорт схемы в XPS-файл с помощью **схемы экспорта как изображения...** пункт контекстного меню в области конструктора представления графа или модели содержимого.

     При экспорте схемы из представления графика в XPS-файл будет экспортирована вся область конструктора. При экспорте схемы из представления модели содержимого, когда область конструктора представления модели содержимого содержит более одного узла, в XPS-файл будет экспортирован только первый узел.

3. Распечатайте сохраненный в XPS-файле образ с использованием средства просмотра XPS.

## <a name="see-also"></a>См. также раздел
 Представление [модели содержимого](../xml-tools/content-model-view.md) представления в виде [диаграммы](../xml-tools/graph-view.md) — [Рабочая область конструктора схем XML](../xml-tools/xml-schema-designer-workspace.md)
