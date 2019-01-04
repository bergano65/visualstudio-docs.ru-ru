---
title: IDebugProgramNode2::GetEngineInfo | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f461bf24df12732085416c12f60219973163d819
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848013"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Возвращает имя и идентификатор для обработчика отладки (DE), выполнение программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrEngine`  
 [out] Возвращает имя DE, выполнение программы (характерным для C++: это может быть указателем null, указывающее, что вызывающему объекту не требуется имя ядро).  
  
 `pguidEngine`  
 [out] Возвращает глобальный уникальный идентификатор DE, выполнение программы (характерным для C++: это может быть указателем null, указывающее, что вызывающий объект не заинтересован в идентификатор GUID модуля).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)