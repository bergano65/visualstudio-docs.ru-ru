---
title: IDebugProgramPublisher2::UnpublishProgram | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2daec6615f98d6e253e65bdc66cb7f1f545f9857
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822219"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Делает недоступной для отладки программы.  
  
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
 [in] `IUnknown` Интерфейс для программы. Это то же значение, передаваемое [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) метод и однозначно идентифицирует программу удаления (то есть он используется как файл cookie).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Чтобы сделать программы доступными для обработчикам отладки и диспетчер отладки сеансов, используйте [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)