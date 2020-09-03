---
title: 'Иивисуализерсервице:: Жетвалуедисплайстрингкаунт | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6785be367430443f92a9cc54a2d636582053228e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192099"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает количество строк значений, отображаемых для указанного свойства или поля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```csharp  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `displayKind`  
 окне Значение из перечисления [дисплайкинд](../../../extensibility/debugger/reference/displaykind.md) .  
  
 `propertyOrField`  
 окне Интерфейс [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий свойство или поле.  
  
 `pcelt`  
 заполняет Возвращает число отображаемых строк значений.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
