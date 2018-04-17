---
title: IDebugPortPicker | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7d9a5a830d6b3b0d191b5eae84bf625ffdb3b695
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
|Метод|Описание|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Отображает указанный диалоговое окно, позволяющий пользователю выбрать порт.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Задает поставщик услуг.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll