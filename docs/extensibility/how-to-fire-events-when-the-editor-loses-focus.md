---
title: 'Как: инициируют события, когда редактор теряет фокус | Документы Microsoft'
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
ms.openlocfilehash: bbdcf30443bc548fd8d182db301cbc7119d8ceae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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