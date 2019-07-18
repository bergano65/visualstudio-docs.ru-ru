---
title: Практическое руководство. Использование меток текста | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c3c4f3a3d9a253b9ec671892d0d44ccf9ca3ab
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430963"
---
# <a name="how-to-use-text-markers"></a>Практическое руководство. Использовать текстовые метки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Текстовые метки, которые могут применяться для редактирования <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> объекта.  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-apply-text-markers"></a>Для применения меток текста  
  
1. Получить экземпляр <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> класса.  
  
    > [!NOTE]
    > Базовый редактор автоматически применяет стандартные текстовые метки в любой документ, он изменяет, и не должен быть необходимую, чтобы явным образом применить стандартные текстовые метки.  
  
2. Получить ИД типа маркера маркера, вам нужны, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> метод с `GUID` вы хотите работать с текстового маркера.  
  
    > [!NOTE]
    > Не используйте `GUID` VSPackage или служба, предоставляющая текстового маркера.  
  
3. Используйте идентификатор типа маркера, полученного путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> методу в качестве параметра для вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метод или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> метод, чтобы применить текстового маркера в зависимости от региона текста.  
  
#### <a name="to-add-features-to-text-markers"></a>Чтобы добавить компоненты в текстовые метки  
  
1. Может потребоваться добавить дополнительные функции для текстового маркера, например всплывающие подсказки, специальные контекстного меню или обработчик для особых случаев. Для этого сделайте следующее:  
  
2. Создайте объект, реализующий интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс.  
  
3. При необходимости дополнительные функциональные возможности реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> интерфейсов на тот же объект, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс.  
  
4. Передайте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс, который создается, чтобы вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метод или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> метод, используемый для применения текстового маркера в зависимости от региона текста.  
  
5. При добавлении поддержки контекстное меню области текстового маркера необходимо создать в меню.  
  
     Дополнительные сведения о том, как создать контекстное меню см. в разделе [контекстные меню](../extensibility/context-menus.md).  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Среда вызывает методы из предоставленных интерфейсов, таких как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> метод, или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> метод, при необходимости.  
  
## <a name="see-also"></a>См. также  
 [С помощью меток текста с помощью API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Практическое руководство. Добавление маркеров стандартного текста](../extensibility/how-to-add-standard-text-markers.md)   
 [Практическое руководство. Создание настраиваемых текстовых маркеров](../extensibility/how-to-create-custom-text-markers.md)   
 [Практическое руководство. Реализация маркеров ошибок](../extensibility/how-to-implement-error-markers.md)
