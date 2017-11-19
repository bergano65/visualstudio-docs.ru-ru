---
title: "Как: инициируют события, когда редактор теряет фокус | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a566d52dc1aabb9895e2f1f9751fdb37ae016d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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