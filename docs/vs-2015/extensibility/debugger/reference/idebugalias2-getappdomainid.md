---
title: IDebugAlias2::GetAppDomainId | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8a2c766a1ec6fce1856312756adad3c5f234866
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557516"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugAlias2::GetAppDomainId](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugalias2-getappdomainid).  
  
Извлекает идентификатор для домена приложения.  
  
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
 [out] Возвращает идентификатор домена приложения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Изменение идентификатора домена приложения при каждом перезапуске приложения, а также новый домен приложения создается.  
  
## <a name="see-also"></a>См. также  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)

