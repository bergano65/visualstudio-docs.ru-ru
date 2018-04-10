---
title: Доступ к слои текста с помощью API прежних версий | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8a5f7a80e8d594f3c9e62ecd2047cc1116948d2c
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Доступ к слои текста с помощью API прежних версий
Слой текста обычно включает в себя некоторые аспекты макет текста. Например слой «функции в раз» скрытие текста до и после функции, содержащее знак вставки (курсора).  
  
 Текстового слоя располагается между буфера и представления, и он изменяет способ представления видит содержимое буфера.  
  
## <a name="text-layer-information"></a>Текстовая информация слоя  
 В следующем списке описываются принципы работы слои текста в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Текст в текстового слоя можно снабженных Цветовая подсветка синтаксиса и маркеры.  
  
-   В настоящее время не могут реализовывать собственные слои.  
  
-   Предоставляет слой <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, который является производным от <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. Буфер текста также реализуется как уровень, который дает возможность просматривать полиморфно выполнение базовых уровнях.  
  
-   Любое количество уровней может лежать между представлением и размер буфера. Каждый слой работает только с уровня и представлении главным образом посвящена самого верхнего уровня. (Это представление обязательно некоторые сведения о буфере).  
  
-   Слой может повлиять на только слои, расположенные под ней. Оно не влияет на слои над ним помимо исходящие стандартные события.  
  
-   В редакторе скрытый текст, синтетические текст и перенос по словам реализуются как слои. Скрытые и синтетические текста можно реализовать без непосредственного взаимодействия с слои. Дополнительные сведения см. в разделе [структуризация в языковую службу прежних версий](../extensibility/internals/outlining-in-a-legacy-language-service.md) и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Каждый слой текст имеет свой собственный локальной системе координат, доступных через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> интерфейса. Уровень переноса строки, например, могут содержаться две строки, а основной текстовый буфер может содержать только одну строку.  
  
-   Представление взаимодействует со слоями через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> интерфейса. Этот интерфейс можно используйте для согласования координат представления с координатами буфер.  
  
-   Любой слоев, такие как слой искусственных текста, рассчитанная текста необходимо предоставить локальной реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   Помимо <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, необходимо реализовать текстового слоя <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> и инициировать события в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> интерфейса.  
  
## <a name="see-also"></a>См. также  
 [Синтаксис, выделение цветом в редакторах](../extensibility/syntax-coloring-in-custom-editors.md)   
 [С помощью текстовых маркеров с помощью API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Настройка меню и редактор элементов управления с помощью API прежних версий](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)