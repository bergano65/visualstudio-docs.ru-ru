---
title: 'Практическое: инициируют события, когда редактор теряет фокус | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af6abf503bec94cb45638b1e059f545f005cb318
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639660"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Практическое: инициируют события, когда редактор теряет фокус
Иногда бывает необходимо знать, когда редактор теряет фокус на рамку окна. Например может потребоваться для извлечения кода из окна кода после редакторе фокуса на нем. Следующая процедура описывает, как переходить для получения уведомлений о редакторе теряет фокус.  
  
## <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Чтобы активировать событие в ответ на редактор теряет фокус  
  
1.  Мониторинг событий выбора путем получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> объекта из <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> и укажите его в ваш <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> объекта.  
  
3.  При вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, искать `elementid==SEID_WindowFrame`.  
  
4.  Тест `varValueNew` параметр для двух целей:  
  
    1.  Фрейм окна, которую вы ищете.  
  
    2.  Точка, по которому программа теряет выделение для этой рамки окна.