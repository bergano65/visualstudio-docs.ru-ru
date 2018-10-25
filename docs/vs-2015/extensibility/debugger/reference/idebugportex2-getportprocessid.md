---
title: IDebugPortEx2::GetPortProcessId | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3c05442737bfa1bedfff855b2ea27c4d2a480f8e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925673"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает идентификатор процесса сам класс port.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetPortProcessId (   
   DWORD* pdwProcessId  
);  
```  
  
```csharp  
int GetPortProcessId (   
   out uint pdwProcessId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwProcessId`  
 [out] Возвращает идентификатор процесса физического порта сам.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 В среде выполнения Win32 к примеру, этот метод обычно вызывает функцию Win32 `GetCurrentProcessId` получить идентификатор физического процесса.  
  
## <a name="see-also"></a>См. также  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)

