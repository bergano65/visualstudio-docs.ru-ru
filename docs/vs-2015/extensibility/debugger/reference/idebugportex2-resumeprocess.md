---
title: 'IDebugPortEx2:: Ресумепроцесс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEx2::ResumeProcess
helpviewer_keywords:
- IDebugPortEx2::ResumeProcess
ms.assetid: e80a6960-9456-4764-9320-e7b1bd57fe5d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: acd6844ddc980df0e69efd94dd162a7a9f1742ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188482"
---
# <a name="idebugportex2resumeprocess"></a>IDebugPortEx2::ResumeProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возобновляет выполнение процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT ResumeProcess(   
   IDebugProcess2* pPortProcess  
);  
```  
  
```cpp#  
int ResumeProcess(   
   IDebugProcess2 pPortProcess  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pPortProcess`  
 окне Объект [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , представляющий процесс, который необходимо возобновить.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
