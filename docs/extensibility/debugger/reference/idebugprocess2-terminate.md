---
title: "IDebugProcess2::Terminate | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::Terminate
helpviewer_keywords: IDebugProcess2::Terminate
ms.assetid: 5e6bf373-0fe9-4321-b04a-473a65f664d9
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2bdc4fbe8910eba6082c69656c5765c47673f02
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess2terminate"></a>IDebugProcess2::Terminate
Завершает процесс.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 При завершении процесса, завершаются все программы, в рамках процесса; Нет разрешено запускать любой дополнительный код.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)