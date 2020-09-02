---
title: Объект Вскодевиндов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 511c730ec3a11b02d46f5e9c9271c028bb4fa325
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690775"
---
# <a name="vscodewindow-object"></a>Объект VSCodeWindow
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Окно кода — это специализированное окно документа, которое может содержать одно или несколько текстовых представлений, обычно это <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объект.  
  
 В архитектуре окно кода — это окно документа, которое находится в рамке окна. Функционально окно кода — это просто окно документа с дополнительными функциями. В режиме многодокументного интерфейса (MDI) окно кода является дочерним фреймом MDI. Дополнительные сведения см. [в разделе Настройка окон кода с помощью API прежних версий](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 В следующей таблице содержатся интерфейсы в <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> объекте.  
  
|Метод|Описание|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Предоставляет универсальный механизм доступа для определения службы, которая идентифицируется глобальным уникальным идентификатором (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Представляет дочерний интерфейс многодокументного интерфейса (MDI), содержащий одно или несколько представлений кода.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Заполняет рамку окна.|  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Изменение фигур](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
