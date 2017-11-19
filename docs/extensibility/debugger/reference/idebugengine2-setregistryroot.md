---
title: "IDebugEngine2::SetRegistryRoot | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::SetRegistryRoot
helpviewer_keywords: IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb553ea8b461b7b571db4970d38514873f9d467e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
Задает корневой раздел реестра для модуля отладки (DE).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetRegistryRoot(   
   LPCOLESTR pszRegistryRoot  
);  
```  
  
```csharp  
int SetRegistryRoot(   
   string pszRegistryRoot  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszRegistryRoot`  
 [in] Корневой раздел реестра для использования.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод позволяет [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] для указания альтернативного корневая папка реестра, DE следует использовать для получения параметров реестра; например, «HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp».  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)