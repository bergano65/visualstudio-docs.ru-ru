---
title: IDebugProgramPublisher2::UnpublishProgram | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 14fd0c09d9a654e8d8ff7097a8974142f0317901
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Делает недоступным для отладки программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```csharp  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pDebuggeeInterface`  
 [in] `IUnknown` Интерфейс для программы. Это то же значение, передаваемое [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) метод и однозначно определяет программу удаления (то есть, он используется как куки-файл).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Чтобы сделать программу отладчики и диспетчера сеанса отладки, используйте [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)