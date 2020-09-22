---
title: Как использовать текстовые маркеры | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842688"
---
# <a name="how-to-use-text-markers"></a>Практическое руководство. Использование текстовых маркеров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для редактирования объекта можно применить текстовые маркеры <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-apply-text-markers"></a>Применение текстовых маркеров  
  
1. Получите экземпляр <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> класса.  
  
    > [!NOTE]
    > Основной редактор автоматически применяет стандартные маркеры текста к любому редактируемому документу, и нет необходимости явно применять стандартные маркеры текста.  
  
2. Получите идентификатор типа маркера для маркера, который вас интересует, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> метод с помощью `GUID` текстового маркера, с которым вы хотите работать.  
  
    > [!NOTE]
    > Не используйте `GUID` пакет VSPackage или службу, которая предоставляет текстовый маркер.  
  
3. Используйте идентификатор типа маркера, полученный путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> метода в качестве параметра для вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метода или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> метода, чтобы применить текстовый маркер к заданной области текста.  
  
#### <a name="to-add-features-to-text-markers"></a>Добавление компонентов в текстовые маркеры  
  
1. Может потребоваться добавить дополнительные функции в текстовый маркер, например подсказки, специальное контекстное меню или обработчик для особых обстоятельств. Для этого сделайте следующее:  
  
2. Создайте объект, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс.  
  
3. Если требуется дополнительная функциональность, реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> интерфейсы для того же объекта, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс.  
  
4. Передайте созданный <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс в вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метода или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> метод, используемый для применения маркера текста к заданной области текста.  
  
5. При добавлении поддержки контекстного меню в область текстового маркера необходимо создать меню.  
  
     Дополнительные сведения о создании контекстного меню см. в разделе [Контекстные меню](../extensibility/context-menus.md).  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Среда вызывает методы предоставляемых интерфейсов, например <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> метод, или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> метод по мере необходимости.  
  
## <a name="see-also"></a>См. также:  
 [Использование текстовых маркеров с устаревшим API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Руководство. Добавление стандартных текстовых маркеров](../extensibility/how-to-add-standard-text-markers.md)   
 [Как создавать пользовательские маркеры](../extensibility/how-to-create-custom-text-markers.md)   
 [Практическое руководство. Реализация маркеров ошибок](../extensibility/how-to-implement-error-markers.md)
