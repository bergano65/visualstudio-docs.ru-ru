---
title: IDebugSymbolProvider::GetTypeByName | Документация Майкрософт
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
- IDebugSymbolProvider::GetTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetTypeByName method
ms.assetid: b9d88d3b-8b75-484a-b9cc-dc8c0fbb4bc8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e6e27fd06800c2e233bfe9d8e354861f16c01d45
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559735"
---
# <a name="idebugsymbolprovidergettypebyname"></a>IDebugSymbolProvider::GetTypeByName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugSymbolProvider::GetTypeByName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugsymbolprovider-gettypebyname).  
  
Этот метод сопоставляет имя символа типа символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetTypeByName(   
   LPCOLESTR     pszClassName,  
   NAME_MATCH    nameMatch,  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetTypeByName(  
   string          pszClassName,   
   NAME_MATCH      nameMatch,   
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszClassName`  
 [in] Имя символа.  
  
 `nameMatch`  
 [in] Выбирает тип соответствия, например, с учетом регистра. Значение из [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) перечисления.  
  
 `ppField`  
 [out] Возвращает тип символа как [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод является универсальная версия [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md).  
  
## <a name="see-also"></a>См. также  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)   
 [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)

