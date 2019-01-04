---
title: IDebugProgramHost2::GetHostName | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 9853313806cf7fc43e12cd27edb571e1c40deb3b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947638"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Возвращает заголовок, понятное имя или имя файла, размещающего процесса данной программы.  
  
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
 [out] Возвращает имя запрошенного размещающего процесса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 В типичной реализации этого метода `dwType` параметр игнорируется, и возвращается понятное имя хост-компьютера. Другая возможная реализация является передача `dwType` параметр в вызов [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) метод для получения имени.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)