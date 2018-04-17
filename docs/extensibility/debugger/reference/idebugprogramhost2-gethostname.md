---
title: IDebugProgramHost2::GetHostName | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 139c7c991235f57dba670c15721751dca71c550f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Возвращает заголовок, понятное имя или имя файла процесса размещения данной программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwType`  
 [in] Значение из [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) перечисления.  
  
 `pbstrHostName`  
 [out] Возвращает имя запрошенного процесса размещения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 В типичной реализации этого метода `dwType` параметр пропускается и возвращается понятное имя компьютера-узла. Другая возможная реализация заключается в передаче `dwType` параметра вызова [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) метод для получения имени.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)