---
title: 'IDebugAlias2:: Жетаппдомаинид | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 79f6a71376d410f6eb0b524a309f5f6dffcdf614
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197918"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает идентификатор для домена приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```csharp  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pappDomainId`  
 заполняет Возвращает идентификатор домена приложения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Идентификатор домена приложения изменяется при каждом перезапуске приложения и создании нового домена приложения.  
  
## <a name="see-also"></a>См. также:  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
