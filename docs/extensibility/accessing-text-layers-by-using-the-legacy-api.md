---
title: Доступ к слои текста с помощью API прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0ba962ba4c18773b5c85480bce62ab728cab307
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62892237"
---
# <a name="access-text-layers-by-using-the-legacy-api"></a>Уровни доступа текста с помощью предыдущих версий API
Текстовый слой обычно включает в себя некоторые аспекты макета текста. Например уровень «функция в a-time» скрывает текст до и после функции, содержащей курсор (точка вставки текста).

 Текстовый слой располагается между буфером и представлением, и он изменяет способ представления видит содержимое буфера.

## <a name="text-layer-information"></a>Сведения слоя текста
 В следующем списке описываются принципы работы слои текста в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:

- Текст в текстовый слой можно оформить с выделение синтаксиса цветом и маркерами.

- В настоящее время не могут реализовывать собственные слои.

- Предоставляет слой <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, который является производным от <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. Текстовый буфер, сам также реализуется как уровень, который дает возможность просматривать полиморфно дело базовых уровней.

- Любое количество уровней может лежать между представлением и буфера. Каждый уровень имеет дело только с уровнем ниже, а представление главным образом посвящена самый высокий уровень. (Представления имеют некоторые сведения о буфере).

- Слой может повлиять на только те слои, которые ниже его. Оно не влияет на слои над ним за исходящий стандартные события.

- В редакторе скрытый текст, синтетического текста и перенос по словам реализуются как слои. Вы можете реализовать скрытых и синтетические текста без непосредственного взаимодействия с слои. Дополнительные сведения см. в разделе [структурирование в языковой службы прежних версий](../extensibility/internals/outlining-in-a-legacy-language-service.md) и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.

- Каждый слой текста имеет свой собственный локальной системе координат, которая доступна посредством <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> интерфейс. Уровень переноса строки, например, могут содержаться две строки, а в базовом текстовом буфере могут содержать только одну строку.

- Представление взаимодействует со слоями через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> интерфейс. Этот интерфейс можно используйте для согласования координатах представления с координатами буфера.

- Любого уровня, такие как слой синтетического текста, который создает текст необходимо предоставить реализацию локального <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.

- Помимо <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, слой текста необходимо реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> и порождают события в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> интерфейс.

## <a name="see-also"></a>См. также
- [Цветовая маркировка синтаксиса в специализированных редакторах](../extensibility/syntax-coloring-in-custom-editors.md)
- [Использование меток текста с предыдущих версий API](../extensibility/using-text-markers-with-the-legacy-api.md)
- [Настройка меню и редактор элементов управления с помощью предыдущих версий API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)