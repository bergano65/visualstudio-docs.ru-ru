---
title: IDebugPortPicker | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 61973b6b9d7c62e8276f46443d0b9520419d3934
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Представляет настраиваемый пользовательский Интерфейс для выбора порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется поставщикам портов. Поставщика порта определяет их выбора порта и предоставление его в качестве идентификатора класса CLSID `metricPortPickerCLSID` метрики на предоставленного идентификатора CLSID.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugPortPicker`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Отображает указанный диалоговое окно, позволяющий пользователю выбрать порт.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Задает поставщик услуг.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll