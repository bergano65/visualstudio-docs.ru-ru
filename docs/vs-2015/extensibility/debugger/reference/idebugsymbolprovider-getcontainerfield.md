---
title: IDebugSymbolProvider::GetContainerField | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugSymbolProvider::GetContainerField
helpviewer_keywords:
- IDebugSymbolProvider::GetContainerField method
ms.assetid: d6b56b4f-a96b-4fa7-87c1-bac4e58fa766
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 294448cb176922596fe5c2170d433e13dc938c45
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572482"
---
# <a name="idebugsymbolprovidergetcontainerfield"></a>IDebugSymbolProvider::GetContainerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugSymbolProvider::GetContainerField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield).  
  
Этот метод возвращает поле, содержащее адрес отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetContainerField(   
   IDebugAddress*         pAddress,  
   IDebugContainerField** ppContainerField  
);  
```  
  
```csharp  
int GetContainerField(  
   IDebugAddress            pAddress,   
   out IDebugContainerField ppContainerField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pAddress`  
 [in] Адрес, представленный [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.  
  
 `ppContainerField`  
 [out] Возвращает контейнер поля, представленного [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

