---
title: Доступ к слои текста с помощью API прежних версий | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5eb9d92e3604224f3806cf64f2dd8d4529e8d01
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729074"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Доступ к слои текста с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Текстовый слой обычно включает в себя некоторые аспекты макета текста. Например уровень «функция в a-time» скрывает текст до и после функции, содержащей курсор (точка вставки текста).  
  
 Текстовый слой располагается между буфером и представлением, и он изменяет способ представления видит содержимое буфера.  
  
## <a name="text-layer-information"></a>Сведения слоя текста  
 В следующем списке описываются принципы работы слои текста в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
-   Текст в текстовый слой можно оформить с выделение синтаксиса цветом и маркерами.  
  
-   В настоящее время не могут реализовывать собственные слои.  
  
-   Предоставляет слой <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, который является производным от <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. Текстовый буфер, сам также реализуется как уровень, который дает возможность просматривать полиморфно дело базовых уровней.  
  
-   Любое количество уровней может лежать между представлением и буфера. Каждый уровень имеет дело только с уровнем ниже, а представление главным образом посвящена самый высокий уровень. (Представления имеют некоторые сведения о буфере).  
  
-   Слой может повлиять на только те слои, которые ниже его. Оно не влияет на слои над ним за исходящий стандартные события.  
  
-   В редакторе скрытый текст, синтетического текста и перенос по словам реализуются как слои. Вы можете реализовать скрытых и синтетические текста без непосредственного взаимодействия с слои. Дополнительные сведения см. в разделе [структурирование в языковой службе прежних версий](../extensibility/internals/outlining-in-a-legacy-language-service.md) и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Каждый слой текста имеет свой собственный локальной системе координат, которая доступна посредством <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> интерфейс. Уровень переноса строки, например, могут содержаться две строки, а в базовом текстовом буфере могут содержать только одну строку.  
  
-   Представление взаимодействует со слоями через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> интерфейс. Этот интерфейс можно используйте для согласования координатах представления с координатами буфера.  
  
-   Любого уровня, такие как слой синтетического текста, который создает текст необходимо предоставить реализацию локального <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   Помимо <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, слой текста необходимо реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> и порождают события в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> интерфейс.  
  
## <a name="see-also"></a>См. также  
 [Цветовая маркировка синтаксиса в специализированных редакторах](../extensibility/syntax-coloring-in-custom-editors.md)   
 [С помощью меток текста с помощью API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Настройка меню и элементов управления редактора с помощью API прежних версий](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)

