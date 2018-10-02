---
title: IDebugBinder3::FindAlias | Документация Майкрософт
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
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d638ed77b2ddcab54431862a26cdbab8a356e4ea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563880"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugBinder3::FindAlias](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder3-findalias).  
  
Этот метод осуществляет поиск псевдоним, заданному имени. Таким образом, найти все псевдонимы в программе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcstrName`  
 [in] Имя псевдонима для поиска.  
  
 `ppAlias`  
 [out] Представленный псевдоним, найденный (если таковые имеются) [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) интерфейс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` (Если псевдоним не найден) или код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод инициализирует в целевой объект, значение null перед вызовом метода; Затем проверяется значение null, впоследствии определить, был ли найден псевдоним.  
  
## <a name="see-also"></a>См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

