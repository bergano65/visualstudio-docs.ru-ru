---
title: Как запускать события при потере фокуса редактором | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204193"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Практическое руководство. Инициация событий, когда редактор теряет фокус
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Иногда необходимо выяснить, когда редактор теряет фокус на фрейме окна. Например, может потребоваться извлечь код из окна кода, когда редактор больше не фокусируется на нем. Следующая процедура позволяет получить уведомление о том, что редактор теряет фокус.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Запуск события в ответ на потерю фокуса редактором  
  
1. Отслеживайте события выбора, получая <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> объект из <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> .  
  
2. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> и укажите свой <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> объект.  
  
3. При вызове функции <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> найдите `elementid==SEID_WindowFrame` .  
  
4. Проверьте `varValueNew` параметр на наличие двух вещей:  
  
    1. Искомая рамка окна.  
  
    2. Точка, в которой программа теряет выделение в рамке окна.
