---
title: "Как: использовать маркеры текст | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1070a88f1bae27b9ff10fedbf6a383ec30c1ed0e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-text-markers"></a>Как: использовать маркеры текста
Маркеры текст может применяться для редактирования <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> объекта.  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-apply-text-markers"></a>Чтобы применить текстовых маркеров:  
  
1.  Получение экземпляра <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> класса.  
  
    > [!NOTE]
    >  Базовый редактор автоматически применяет маркеры стандартный текст в любой документ, он изменяет, и необходимо необходимо явным образом применить маркеры стандартного текста.  
  
2.  Получить идентификатор типа маркера маркера интересуют путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> метод с `GUID` текстовой метки, которые вы хотите работать с.  
  
    > [!NOTE]
    >  Не используйте `GUID` VSPackage или службу, которая предоставляет текстовой метки.  
  
3.  Используйте идентификатор типа маркера, полученного путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> методу в качестве параметра для вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метода или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> метод, применяемый для данной области текста текстовая метка.  
  
#### <a name="to-add-features-to-text-markers"></a>Чтобы добавить компоненты в текстовых маркеров:  
  
1.  Может потребоваться добавить дополнительные компоненты в текстовая метка, таких как всплывающие подсказки, специальные контекстного меню или обработчик в особых обстоятельствах. Для этого:  
  
2.  Создать объект, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейса.  
  
3.  При необходимости дополнительные функциональные возможности реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> интерфейсов на тот же объект, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейса.  
  
4.  Передайте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс, который создается, чтобы вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метода или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> метод, используемый для применения к данной области текста текстовой метки.  
  
5.  При добавлении поддержки контекстного меню в область текста маркер необходимо создать в меню.  
  
     Дополнительные сведения о том, как создать контекстное меню см. в разделе [контекстные меню](../extensibility/context-menus.md).  
  
6.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Среда вызывает методы предоставленных интерфейсов, таких как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> метод, или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> метод при необходимости.  
  
## <a name="see-also"></a>См. также  
 [С помощью текстовых маркеров с помощью API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Как: Добавление маркеров стандартного текста](../extensibility/how-to-add-standard-text-markers.md)   
 [Как: Создание настраиваемых текстовых маркеров](../extensibility/how-to-create-custom-text-markers.md)   
 [Как: реализовать маркеры ошибки](../extensibility/how-to-implement-error-markers.md)