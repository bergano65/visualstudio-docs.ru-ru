---
title: IDebugAlias2::GetAppDomainId | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 07c04aff053b8ce304290fefa7f56f08b448f244
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836642"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Извлекает идентификатор для домена приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
 [out] Возвращает идентификатор домена приложения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Изменение идентификатора домена приложения при каждом перезапуске приложения, а также новый домен приложения создается.  
  
## <a name="see-also"></a>См. также  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)