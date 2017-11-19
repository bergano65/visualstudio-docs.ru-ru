---
title: "IDebugPortEx2::ResumeProcess | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEx2::ResumeProcess
helpviewer_keywords: IDebugPortEx2::ResumeProcess
ms.assetid: e80a6960-9456-4764-9320-e7b1bd57fe5d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 02fe1424755f2adc58165587686b195a544a2664
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportex2resumeprocess"></a>IDebugPortEx2::ResumeProcess
Возобновляет выполнение процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT ResumeProcess(   
   IDebugProcess2* pPortProcess  
);  
```  
  
```cpp  
int ResumeProcess(   
   IDebugProcess2 pPortProcess  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pPortProcess`  
 [in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) объекта, представляющего процесс возобновления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)