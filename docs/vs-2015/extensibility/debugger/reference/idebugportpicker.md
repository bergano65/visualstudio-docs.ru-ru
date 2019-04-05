---
title: IDebugPortPicker | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f3e030facd8c70aec4fdc480b01c90ee4c0acda7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980482"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Представляет настраиваемый пользовательский Интерфейс для выбора порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется поставщикам портов. Поставщика порта определяет их выбора порта предоставлением в качестве идентификатора класса CLSID, и выберите пункт `metricPortPickerCLSID` метрик в предоставленный идентификатор CLSID.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugPortPicker`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Отображает указанный диалоговое окно, которое позволяет пользователю выбрать порт.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Задает поставщик службы.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
