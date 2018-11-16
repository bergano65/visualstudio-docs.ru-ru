---
title: IDebugEngine2::GetEngineID | Документация Майкрософт
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
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 00a99d1b9456fd529d079197433db919c9e29c84
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750495"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает идентификатор GUID модуля отладки (DE).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetEngineID(   
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineID(   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pguidEngine`  
 [out] Возвращает идентификатор GUID DE.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Некоторые примеры типичных GUID: `guidScriptEng`, `guidNativeEng`, или `guidSQLEng`. Новый отладчиков создаст собственные GUID для идентификации.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простого `CEngine` объект, реализующий [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) интерфейс.  
  
```cpp#  
HRESULT CEngine::GetEngineId(GUID *pguidEngine){    
   if (pguidEngine) {    
      // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.    
      // Other languages would require their own guidDifferentEngine to be  
      //defined in the Batdbg.idl file.    
      *pguidEngine = guidBatEng;    
      return NOERROR; // This is typically S_OK.    
   } else {  
      return E_INVALIDARG;    
   }    
}    
```  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

