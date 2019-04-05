---
title: IDebugProgramHost2::GetHostName | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb7ceae40282115dc455691789c3882a1620e829
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994231"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает заголовок, понятное имя или имя файла, размещающего процесса данной программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
