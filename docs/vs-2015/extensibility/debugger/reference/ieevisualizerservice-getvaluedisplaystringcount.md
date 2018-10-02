---
title: IEEVisualizerService::GetValueDisplayStringCount | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4bcf1eae6d948b40cc64f5eadf1c2b3e5a0fd206
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559685"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IEEVisualizerService::GetValueDisplayStringCount](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount).  
  
Возвращает номер строки значение указанного свойства или поля.  
  
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
 [in] Значение из [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) перечисления.  
  
 `propertyOrField`  
 [in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс, который представляет свойство или поле.  
  
 `pcelt`  
 [out] Возвращает число строк, значение для отображения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)

