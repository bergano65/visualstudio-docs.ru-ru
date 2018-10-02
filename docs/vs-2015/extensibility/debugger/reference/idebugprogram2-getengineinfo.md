---
title: IDebugProgram2::GetEngineInfo | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::GetEngineInfo
helpviewer_keywords:
- IDebugProgram2::GetEngineInfo
ms.assetid: 3a4f2dc0-e082-4d8d-aeaf-463ab09d279b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e242a0d2fa414e4f735d5964d65308a68b58d774
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570038"
---
# <a name="idebugprogram2getengineinfo"></a>IDebugProgram2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProgram2::GetEngineInfo](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-getengineinfo).  
  
Возвращает имя и идентификатор GUID для обработчика отладки (DE), выполнение программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetEngineInfo(   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(   
   out string pbstrEngine,  
   out GUID   pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrEngine`  
 [out] Возвращает имя DE, выполнение программы.  
  
 `pguidEngine`  
 [out] Возвращает идентификатор GUID для DE, выполнение программы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Каждый DE определяет собственный идентификатор GUID для идентификации.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

