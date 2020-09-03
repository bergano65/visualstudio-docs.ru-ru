---
title: Доступ к текстовым слоям с помощью API прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 975e8624a6ffbfe0c5ae7544f2b978487465e34e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148024"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Доступ к слоям текста с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Текстовый слой обычно инкапсулирует некоторый аспект макета текста. Например, на уровне "функция в любой момент времени" скрывается текст до и после функции, содержащей курсор (точка вставки текста).  
  
 Текстовый слой находится между буфером и представлением и изменяет способ, которым представление видит содержимое буфера.  
  
## <a name="text-layer-information"></a>Сведения о текстовом слое  
 В следующем списке описано, как работают текстовые слои [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Текст в текстовом слое может быть оформлен с помощью цветового выделения и маркеров синтаксиса.  
  
- В настоящее время невозможно реализовать собственные слои.  
  
- Слой предоставляет объект <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> , производный от <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> . Сам текстовый буфер также реализуется как слой, что позволяет представлениям работать полиморфно с базовыми слоями.  
  
- Между представлением и буфером может находиться любое количество слоев. Каждый уровень работает только с уровнем под ним, а представление в основном работает с самым верхним слоем. (Представление содержит некоторые сведения о буфере.)  
  
- Слой может повлиять только на слои, находящиеся под ним. Он не влияет на уровни, расположенные выше, чем стандартные события.  
  
- В редакторе скрытый текст, искусственный текст и перенос по словам реализуются как слои. Можно реализовать скрытый и искусственный текст, не взаимодействуя непосредственно с слоями. Дополнительные сведения см. [в разделе Структурирование в языковой службе прежних версий](../extensibility/internals/outlining-in-a-legacy-language-service.md) и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession> .  
  
- Каждый текстовый слой имеет собственную локальную систему координат, доступную через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> интерфейс. Например, слой переноса строк может содержать две строки, в то время как базовый текстовый буфер может содержать только одну строку.  
  
- Представление взаимодействует с слоями через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> интерфейс. Используйте этот интерфейс для согласования координат представления с координатами буфера.  
  
- Любой слой, такой как искусственный текстовый слой, который является источником текста, должен обеспечивать локальную реализацию <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A> .  
  
- Кроме того <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> , текстовый слой должен реализовывать <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> и вызывать события в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> интерфейсе.  
  
## <a name="see-also"></a>См. также:  
 [Выделение синтаксиса в пользовательских редакторах](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Использование текстовых маркеров с устаревшим API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Настройка меню и элементов управления редактора с помощью API прежних версий](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
