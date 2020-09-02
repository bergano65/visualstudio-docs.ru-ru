---
title: 'IDebugProcess2:: Жетфисикалпроцессид | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetPhysicalProcessId
helpviewer_keywords:
- IDebugProcess2::GetPhysicalProcessId
ms.assetid: 77da6e10-75af-4308-97dd-c44416ca52d7
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 413373dc79ea8e7ed2e5cf1386695896deb96e1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202885"
---
# <a name="idebugprocess2getphysicalprocessid"></a>IDebugProcess2::GetPhysicalProcessId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает идентификатор системного процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetPhysicalProcessId(  
   AD_PROCESS_ID* pdwProcessId  
);  
```  
  
```csharp  
int GetPhysicalProcessId(  
   AD_PROCESS_ID[] pdwProcessId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwProcessId`  
 заполняет Структура [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) , которая заполняется сведениями об идентификаторе системного процесса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
