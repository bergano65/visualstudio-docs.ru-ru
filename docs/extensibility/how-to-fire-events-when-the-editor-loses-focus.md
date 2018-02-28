---
title: "Как: инициируют события, когда редактор теряет фокус | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bb20adf3950e87c37e2ca64bcd78913839f89d01
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Как: инициируют события, когда редактор теряет фокус
Иногда бывает необходимо знать, когда редактор теряет фокус на фрейм окна. Например может потребоваться извлечь код из окна кода после редактор больше не занимается ее. Далее описаны действия для получения уведомлений о потере фокуса редактора.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Для порождения события в ответ на редактор теряет фокусировку  
  
1.  Мониторинг событий выбора, получая <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> объекта из <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> и предоставить ему вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> объекта.  
  
3.  При вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, искать `elementid==SEID_WindowFrame`.  
  
4.  Тест `varValueNew` параметров для двух целей:  
  
    1.  Рамка окна, которую вы ищете.  
  
    2.  Точка, с которой программа теряет выделения до этого фрейма окна.