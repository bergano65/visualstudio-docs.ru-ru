---
title: IDebugProgramNode2::GetEngineInfo | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 687ae8207fac97dde84b803fb01477d53114ad6e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847974"
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