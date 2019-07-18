---
title: Практическое руководство. Инициируют события, когда редактор теряет фокус | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ebca733798636ca32787b88b8874c31a2ffffdb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204193"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Практическое руководство. Инициация событий, когда редактор теряет фокус
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Иногда бывает необходимо знать, когда редактор теряет фокус на рамку окна. Например может потребоваться для извлечения кода из окна кода после редакторе фокуса на нем. Следующая процедура описывает, как переходить для получения уведомлений о редакторе теряет фокус.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Чтобы активировать событие в ответ на редактор теряет фокус  
  
1. Мониторинг событий выбора путем получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> объекта из <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> и укажите его в ваш <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> объекта.  
  
3. При вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, искать `elementid==SEID_WindowFrame`.  
  
4. Тест `varValueNew` параметр для двух целей:  
  
    1. Фрейм окна, которую вы ищете.  
  
    2. Точка, по которому программа теряет выделение для этой рамки окна.
