---
title: Практическое руководство. Использование меток текста | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0bd8a9bb1410ef91883e4ec46fa6be85ac828b6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324628"
---
# <a name="how-to-use-text-markers"></a>Практическое руководство. Использовать текстовые метки
Текстовые метки, которые могут применяться для редактирования <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> объекта.

## <a name="procedures"></a>Процедуры

### <a name="to-apply-text-markers"></a>Для применения меток текста

1. Получить экземпляр <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> класса.

    > [!NOTE]
    > Базовый редактор автоматически применяет стандартные текстовые метки в любой документ, он изменяет, и не должен быть необходимую, чтобы явным образом применить стандартные текстовые метки.

2. Получить ИД типа маркера маркера, вам нужны, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> метод с `GUID` вы хотите работать с текстового маркера.

    > [!NOTE]
    > Не используйте `GUID` VSPackage или служба, предоставляющая текстового маркера.

3. Используйте идентификатор типа маркера, полученного путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> методу в качестве параметра для вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метод или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> метод, чтобы применить текстового маркера в зависимости от региона текста.

### <a name="to-add-features-to-text-markers"></a>Чтобы добавить компоненты в текстовые метки

1. Может потребоваться добавить дополнительные функции для текстового маркера, например всплывающие подсказки, специальные контекстного меню или обработчик для особых случаев. Для этого сделайте следующее:

2. Создайте объект, реализующий интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс.

3. При необходимости дополнительные функциональные возможности реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> интерфейсов на тот же объект, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс.

4. Передайте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс, который создается, чтобы вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метод или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> метод, используемый для применения текстового маркера в зависимости от региона текста.

5. При добавлении поддержки контекстное меню области текстового маркера необходимо создать в меню.

    Дополнительные сведения о том, как создать контекстное меню см. в разделе [контекстные меню](../extensibility/context-menus.md).

6. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Среда вызывает методы из предоставленных интерфейсов, таких как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> метод, или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> метод, при необходимости.

## <a name="see-also"></a>См. также
- [Использование меток текста с предыдущих версий API](../extensibility/using-text-markers-with-the-legacy-api.md)
- [Практическое руководство. Добавление маркеров стандартного текста](../extensibility/how-to-add-standard-text-markers.md)
- [Практическое руководство. Создание настраиваемых текстовых маркеров](../extensibility/how-to-create-custom-text-markers.md)
- [Практическое руководство. Реализовать маркеры ошибок](../extensibility/how-to-implement-error-markers.md)